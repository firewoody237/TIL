# 1. 스레드와 큐를 이용한 업무 스킬
> 데이터의 수신과 송신을 `스레드`로 `병렬처리`한다. (스레드 `큐`사용)

<br>

```c#
namespace threadQueue
{
    public partial class Form1 : Form
    {

        AutoResetEvent autoResetEvent = new AutoResetEvent(false);
        Queue<string> queue = new Queue<string>();
        Thread thread = null;

        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            thread = new Thread(new ThreadStart(Logic));
            thread.IsBackground = true;
            thread.Start();
        }

        //프로토콜 데이터를 수신해서 처리
        private void Logic()
        {
            while(true)
            {
                int queueCount = 0;

                lock(queue)
                {
                    queueCount = queue.Count;
                }

                if(queueCount == 0)
                {
                    this.Invoke(new Action(() =>
                    {
                        label1.Text = "대기중";
                    }));
                    //데이터가 들어올 때 까지 대기.
                    //처리할 데이터가 X
                    autoResetEvent.WaitOne();
                }
                else
                {
                    //TCP 프로토콜 형태로 다른 시스템에 전달
                    //DB에 데이터를 저장
                    //파일에 데이터를 저장
                    //오래 걸릴 가능성 O
                    this.Invoke(new Action(() =>
                    {
                        label2.Text += queue.Dequeue();
                    }));
                }
            }
        }

        //프로토콜 데이터를 수신한다고 가정
        //TCP로부터 데이터를 수신, UDP네트워크 통신, Serial 프로토콜로 데이터를 수신
        private void button1_Click(object sender, EventArgs e)
        {
            //프로토콜로 받은 데이터를 수신 후 queue에 넣게 됨
            queue.Enqueue("100");
            autoResetEvent.Set();
        }
    }
}
```

<br><br>

# 2. 네트워크

* `OSI 7 Layer`로 데이터를 주고받음 (응용계층 / 표현계층 / 세션계층 / 전송계층 / 네트워크계층 / 데이터링크계층 / 물리계층)
* `TCP` : 신뢰성 보장(3 hand shake) - 이상하면 재전송
* `UDP` : 신뢰성을 보장 X

## TCP

1. `TcpClient` : 가볍고 사용하기 쉬운 클래스, Socket 클래스보다 덜 유연함, 자주 사용하지 않음
2. `Socket` : 주로 사용

**TCP 연결 순서**
1. 클라이언트 소켓 생성
2. 서버 소켓 생성
3. 클라이언트 연결 요청
4. 서버에서 클라이언트마다 소켓 별도로 생성

**Client**
```c#
namespace MYTCP
{
    internal class Client
    {
        //이벤트
        public delegate void ConnectedHandler(Socket socket);
        public delegate void DisconnectedHandler(string disconnectMsg);
        public delegate void ReceivededHandler(byte[] bytes);
        public event ConnectedHandler OnConnected;
        public event DisconnectedHandler OnDisconnected;
        public event ReceivededHandler OnReceive;

        private Socket socket = null;
        private string ip = "";
        private int port = 43210;
        private Thread thread = null;
        private bool stop = false; //클라이언트의 연결 상태

        public Client(string ipAddress, int port)
        {
            this.ip = ipAddress;
            this.port = port;

            socket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
        }

        public void Start()
        {
            try
            {
                //연결될 곳의 IP주소와 Port를 가지고 있는 클래스
                IPEndPoint remoteEp = new IPEndPoint(IPAddress.Parse(ip), port);
                socket.Connect(remoteEp); //서버 프로그램이라면 비동기인 BeginConnect

                if (OnConnected != null)
                {

                    //연결되면 이븐트를 통해서 사용하는 곳에 알려준다.
                    OnConnected(socket);
                }

                thread = new Thread(ReceiveMessage);
                thread.IsBackground = true;
                thread.Start();
            }
            catch (Exception)
            {
                throw;
            }
            
        }

        //데이터수신 함수
        private void ReceiveMessage()
        {
            while(!stop)
            {
                try
                {
                    byte[] buffer = new byte[1024];
                    int byteRead = socket.Receive(buffer, 0, buffer.Length, SocketFlags.None);
                    if (byteRead <= 0)
                    {
                        throw new SocketException();
                    }

                    Array.Resize(ref buffer, byteRead);

                    if (OnReceive != null)
                    {
                        OnReceive(buffer);
                    }
                }
                catch
                {
                    if(OnDisconnected != null)
                    {
                        OnDisconnected("DisConnected");
                    }
                    if (socket != null)
                    {
                        socket.Close();
                    }
                    break;
                }
            }
            this.Stop();
        }

        public void Stop()
        {
            stop = true;
            if(socket != null)
            {
                socket.Close();
                socket.Dispose();
            }
            socket = null;

            //수신하는 스레드 정지
            if(thread!=null)
            {
                thread.Abort();
            }
            thread = null;
        }

        internal void SendMessage(string message)
        {
            int bytesSend = socket.Send(Encoding.UTF8.GetBytes(message));

        }
    }
}
```

**Client Form**
```c#
namespace MYTCP
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }
        Client client = null;

        private void button1_Click(object sender, EventArgs e)
        {
            Start();
        }

        private void Start()
        {
            if(client == null)
            {
                client = new Client(textBox1.Text, Int32.Parse(textBox2.Text));
                client.OnConnected += TcpConnected;
                client.OnDisconnected += TcpDisConnected;
                client.OnReceive += TcpReceived;
                client.Start();
            }
        }

        private void TcpReceived(byte[] bytes)
        {
            this.BeginInvoke(new Action(() =>
            {
                richTextBox1.Text += "[Local]수신메시지-" + Encoding.UTF8.GetString(bytes) + "\r\n";
            }));
            
        }

        private void TcpDisConnected(string disconnectMsg)
        {
            this.BeginInvoke(new Action(() =>
            {
                Stop();
                richTextBox1.Text += "[Local]서버 접속 해제됨" + "\r\n";
            }));
            client = null;
        }

        private void Stop()
        {
            if (client != null)
            {
                client.Stop();
            }
            client = null;
        }

        private void TcpConnected(Socket socket)
        {
            this.BeginInvoke(new Action(() =>
            {
                richTextBox1.Text += "[Local]서버접속 성공.\r\n";
            }));
        }

        private void button2_Click(object sender, EventArgs e)
        {
            Stop();
        }

        private void button3_Click(object sender, EventArgs e)
        {
            if(client != null)
            {
                client.SendMessage(textBox3.Text);
            }
        }
    }
}
```

**Server**
```c#
namespace TCPServer
{
    public class TcpListener
    {

        public delegate void AcceptedHandler(Socket e);
        public event AcceptedHandler OnAccepted;
        Socket _socket;
        int _port = 43210;

        public TcpListener(int port)
        {
            _socket = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
            _port = port;
        }

        public void Start(string serverIp)
        {
            _socket.Bind(new IPEndPoint(IPAddress.Parse(serverIp), _port));
            _socket.Listen(5); //연결이 이뤄질동안 대기할 Client수 지정
            _socket.BeginAccept(ConnectCallback, null); //비동기적으로 연결에 대한것 처리
        }

        public void ConnectCallback(IAsyncResult ar)
        {
            try
            {
                //데이터를 주고받을 때 사용할 Socket
                Socket client = _socket.EndAccept(ar);

                if (OnAccepted != null)
                {
                    OnAccepted(client);
                }

                //콜백방식 : 어떠한 작업을 하고나서 이후작업
                _socket.BeginAccept(ConnectCallback, null);
            }
            catch (Exception)
            {

            }
            
        }
    }
}

```

**Server Form**

```c#
namespace TCPServer
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        TcpListener tcpListener = null;

        private void Form1_Load(object sender, EventArgs e)
        {
            tcpListener = new TcpListener(43210);
            tcpListener.OnAccepted += new TcpListener.AcceptedHandler(ClientAccepted);
            tcpListener.Start("127.0.0.1");
        }

        private void ClientAccepted(System.Net.Sockets.Socket socket)
        {
            TcpClient tcpClient = new TcpClient(socket);
            tcpClient.OnReceived += new TcpClient.ReceivedHandler(ClientReceived);

            this.Invoke(new Action(() =>
            {
                this.richTextBox2.Text += "" + " [연결완료]: " +tcpClient.IPEndPoint + " ";
                ListViewItem item = new ListViewItem();
                item.Text = tcpClient.IPEndPoint.ToString();
                item.SubItems.Add(tcpClient.IPEndPoint.ToString());
                item.SubItems.Add(tcpClient.id);
                item.Tag = tcpClient; //태그를 통해 tcp Client를 얻을 수 있음
                listView1.Items.Add(item);
            }));

        }

        public void ClientReceived(TcpClient sender, byte[] data)
        {
            this.Invoke(new Action(() =>
            {
                this.richTextBox1.Text += "" + sender.IPEndPoint + " 내용: " + Encoding.UTF8.GetString(data);
            }));
        }
    }
}
```
