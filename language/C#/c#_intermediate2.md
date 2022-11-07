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

