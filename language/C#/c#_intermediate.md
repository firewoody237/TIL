# 1. 멀티스레드
* UIThread 내부에 여러가지 Thread가 `병렬`로 사용 됨
* 서로의 작업에 영향을 주지 않게하고 싶을 때 사용
* 오래걸리는 작업등에 사용(`네트워크` 수신, `DB` 작업 등)

<br>

**쓰레드 문법**
```c#
Thread thread = new Thread(new ThreadStart(GetItemThread))
thread.IsBackground = true; //UIThread와 같이 종료되게 함
thread.Priority = ThreadPriority.Normal; //OS자원 할당의 중요도 설정
thread.Start();
```
`thread.Start()`가 실행되면, `ThreadStart`의 매개 메소드가 실행 됨

<br>

**예제**
```c#
namespace CSStudy
{
    public partial class Form1 : Form
    {
        Thread thread1 = null;
        Thread thread2 = null;

        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            thread1 = new Thread(new ThreadStart(WorkThread));
            thread1.IsBackground = true;
            thread1.Priority = ThreadPriority.Normal;
            thread1.Start();

            thread2 = new Thread(new ThreadStart(WorkThread2));
            thread2.IsBackground = true;
            thread2.Priority = ThreadPriority.Normal;
            thread2.Start();

            Thread.Sleep(3000);
            MessageBox.Show("Print when Form Loaded!");
        }

        private void WorkThread()
        {
            Thread.Sleep(3000);
            MessageBox.Show("Print in Thread Method1");
        }

        private void WorkThread2()
        {
            Thread.Sleep(2000);
            MessageBox.Show("Print from Thread Method2");
        }
    }
}
```

<br>

`Form1`에서 `new Form2`로 `Form2`를 호출하는 경우, `Form2`자체도 하나의 쓰레드다. 

따라서 `UIThread`인 `Form1`가 멈추면 `Form2`도 제대로 동작하지 않는다.

<br><br>

# 2. 스레드 동기화
* `여러 스레드`가 `리소스`를 공유할 때, 공유 리소스를 `안전(Thread Safe)`하게 액세스
* 공유 자원을 `임계 영역`으로 설정
* 특정 스레드가 공유 자원을 사용할 때, 자원을 `독점`

<br>

## lock
> 동기화에 사용할 `객체`를 선언하고, 해당 객체를
> 
> `lock(객체)`로 잠궈서 사용
> 
> `DeadLock`의 위험성이 있으니 조심히 사용

<br>

**아래와 같은 경우에 사용**
* 파일 읽고 쓰기
* 네트워크 송, 수신
* DB 작업

```c#
namespace CSStudy
{
    public partial class Form1 : Form
    {
        int sharedValue = 5;
        object lockObj = new object();

        Thread thread1 = null;
        Thread thread2 = null;

        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            thread1 = new Thread(new ThreadStart(WorkThread1));
            thread1.IsBackground = true;
            thread1.Priority = ThreadPriority.Normal;
            thread1.Start();

            thread2 = new Thread(new ThreadStart(WorkThread2));
            thread2.IsBackground = true;
            thread2.Priority = ThreadPriority.Normal;
            thread2.Start();
        }

        private void WorkThread1()
        {
            while (true)
            {
                lock (lockObj)
                {
                    Thread.Sleep(4000);
                    sharedValue = 1;
                }
            }
        }

        private void WorkThread2()
        {
            while(true)
            {
                lock (lockObj)
                {
                    sharedValue = 2;
                    Thread.Sleep(4000);
                    MessageBox.Show($"Print from Thread Method2 + {sharedValue}");
                }
            }
        }
    }
}
```

<br>

**순서**

`WorkThread1`에서 `lock`

-> `WorkThread2`에서 실행하려 하지만, `lock`이 풀릴 때 까지 대기

-> `WorkThread1`의 작업이 끝나면, `WorkThread2`가 자원을 `lock`한 뒤 작업 진행

<br>

## AutoResetEvent

```c#
AutoResetEvent autoResetEvent = new AutoResetEvent(false);
autoResetEvent.Set(); //신호를 보냄
autoResetEvent.WaitOne(); //신호를 받을 때까지 대기
//첫 번째 신호는 받은 상태로 변경
//두 번째 신호를 대기하는 상태
```

**예제**

```c#
namespace CSStudy
{
    public partial class Form1 : Form
    {
        AutoResetEvent autoResetEvent = new AutoResetEvent(false);

        Thread thread1 = null;
        Thread thread2 = null;

        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            thread1 = new Thread(new ThreadStart(WorkThread1));
            thread1.IsBackground = true;
            thread1.Priority = ThreadPriority.Normal;
            thread1.Start();

            thread2 = new Thread(new ThreadStart(WorkThread2));
            thread2.IsBackground = true;
            thread2.Priority = ThreadPriority.Normal;
            thread2.Start();
        }

        private void WorkThread1()
        {
            while (true)
            {
                autoResetEvent.WaitOne(); //신호를 받을 때까지 대기
                MessageBox.Show(sharedValue.ToString());
            }
        }

        private void WorkThread2()
        {
            while(true)
            {
                Thread.Sleep(2000);
                autoResetEvent.Set(); //신호를 보냄
            }
        }
    }
}
```

<br><br>

# 3. 동기, 비동기
> `동기(Invoke, Sync)` : 작업의 순서대로 수행
> 
> `비동기(BeginInvoke, Async)` : 작업을 병렬로 수행

<br>

**예제**

```c#
namespace CSStudy
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        delegate void MySettingDelegate(string str);

        private void Form1_Load(object sender, EventArgs e)
        {
            string myString = "aa";
            //비동기
            MySettingDelegate mySettingDelegate = MySetting;

            mySettingDelegate.BeginInvoke(myString, null, null);

            label1.Text = myString;
        }
        private void MySetting(string str)
        {
            for(int i = 0; i < 100; i++)
            {
                str += "aa";
                Thread.Sleep(100);
            }

            this.BeginInvoke((Action)(() =>
            {
                label1.Text = str;
            }));

            this.Invoke((Action)(() =>
            {
                label1.Text = str;
            }));
            //다른 스레드에서 메소드가 실행 됨
            MessageBox.Show("Finished");
            label1.Text = str;
        }
    }
}
```

<br>

## 함수를 동기, 비동기로 실행
> `AsyncCallback` : 비동기 작업이 끝난 후 호출할 함수 지정
> 
> `Callback` : 호출 후 결과 수신, 처리 

* `BeginInvoke`의 내부에 `Callback 함수` 적용 가능
* `AsyncWaitHandle`을 사용해 `비동기` 작업에 대한 `결과`를 확인 가능

<br>


**예제**
```c#
namespace CSStudy
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        delegate void MySettingDelegate(string str);

        private void Form1_Load(object sender, EventArgs e)
        {
            string myString = "aa";

            AsyncCallback callback = new AsyncCallback(Complete);

            //비동기
            MySettingDelegate mySettingDelegate = MySetting;

            IAsyncResult ar = mySettingDelegate.BeginInvoke(myString, callback, "str");
            //첫번째 인자 : 델리게이트의 매개변수
            //두번째 인자 : 콜백함수
            //세번째 인자 : 콜백의 매개변수로 들어감
            bool success = ar.AsyncWaitHandle.WaitOne(TimeSpan.FromSeconds(3));
            //비동기 작업이 3초안에 끝났다면, success == true
            if (success)
            {
                MessageBox.Show("작업 완료");
            }
            
            label1.Text = myString;
        }

        private void Complete(IAsyncResult ar)
        {
            //MySetting -> Complete("str")
            string str = (string)ar.AsyncState; //"str"
            MessageBox.Show(str);
        }

        private void MySetting(string str)
        {
            for(int i = 0; i < 100; i++)
            {
                str += "aa";
            }
            
            this.BeginInvoke((Action)(() =>
            {
                label1.Text = str;
            }));

            this.Invoke((Action)(() =>
            {
                label1.Text = str;
            }));
            Thread.Sleep(5000);
        }
    }
}
```

<br>

# 4. 스레드 문제점 해결

## 스레드 자원 미해제 문제
* 화면은 종료되었으나, 작업이 프로세스에 남아있는 문제

### 방법 1
`thread.IsBackground = true`로 `UIThread`가 종료되면 자동으로 `스레드`도 종료되게 설정

**예제**
```c#
namespace CSStudy
{
    public partial class Form1 : Form
    {
        Thread thread = null;

        public Form1()
        {
            InitializeComponent();
        }


        private void Form1_Load(object sender, EventArgs e)
        {
            thread = new Thread(new ThreadStart(methodStart));
            thread.IsBackground = true;
            thread.Start();
        }

        private void methodStart()
        {
            while (true)
            {
                Thread.Sleep(1000);
                //쓰레드가 계속 실행될 수 있음
            }
        }
    }
}
```

### 방법 2
`스레드`가 `null`인지 확인하여 `해제`하는 코드을 넣어 줌

**예제**
```c#
namespace CSStudy
{
    public partial class Form2 : Form
    {
        Thread thread = null;

        public Form2()
        {
            InitializeComponent();
        }

        private void Form2_Load(object sender, EventArgs e)
        {
            thread = new Thread(new ThreadStart(methodStart));
            thread.IsBackground = true;
            thread.Start();
        }

        private void methodStart()
        {
            while (true)
            {
                Thread.Sleep(1000);
                //쓰레드가 계속 실행될 수 있음
            }
        }

        private void Form2_FormClosing(object sender, FormClosingEventArgs e)
        {
            if(thread != null)
            {
                thread.Abort();
            }
            thread = null;
        }
    }
}
```
위 예제같은 경우는 `Form2`이기 때문에, 따로 `Abort`를 해주지 않으면 백그라운드에 계속 떠있게 됨.

<br>

## 크로스 스레드
> `UI Thread 외 다른 스레드`가 `Controller`의 접근할 경우 발생하는 에러

**예제**
```c#
namespace CSStudy
{
    public partial class Form2 : Form
    {
        Thread thread = null;

        public Form2()
        {
            InitializeComponent();
        }

        private void Form2_Load(object sender, EventArgs e)
        {
            thread = new Thread(new ThreadStart(methodStart));
            thread.IsBackground = true;
            thread.Start();
        }

        private void methodStart()
        {
            //UI Controller에 접근하는 방법 1
            this.Invoke((MethodInvoker)delegate
            {
                label1.Text = "sss";
            });

            //UI Controller에 접근하는 방법 2
            this.Invoke(new Action(() =>
            {
                label1.Text = "sss";
            }));
            
            while (true)
            {
                Thread.Sleep(1000);
                //쓰레드가 계속 실행될 수 있음
            }
        }

        private void Form2_FormClosing(object sender, FormClosingEventArgs e)
        {
            if(thread != null)
            {
                thread.Abort();
            }
            thread = null;
        }
    }
}
```

<br><br>

# 5. 이벤트 생성, 호출

> 다른 클래스에 값을 넘길 수 있음
>
> `이벤트 게시자(Publisher)`와 `이벤트 구독자(Subscriber)`로 구분된다.
> 
> `Form 간`, `Class 간`, `Class <-> dll` 값 전달

**예제**
```c#
/*
Form1.cs
*/

namespace CSStudy
{

    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }


        private void Form1_Load(object sender, EventArgs e)
        {
            Form2 form = new Form2();
            form.MyFirst += Sum;
            form.Show();
        }

        private void Sum(int a)
        {
            label1.Text = a.ToString();
            MessageBox.Show("" + a);
        }
    }
}


/*
Form2.cs
*/

namespace CSStudy
{
    public partial class Form2 : Form
    {

        public delegate void OnMyFirstHandler(int a);
        public event OnMyFirstHandler MyFirst;

        Thread thread = null;

        public Form2()
        {
            InitializeComponent();
        }

        private void Form2_Load(object sender, EventArgs e)
        {
            thread = new Thread(new ThreadStart(MyTest));
            thread.IsBackground = true;
            thread.Start();
        }

        private void MyTest()
        {
            MyFirst(5);
        }
    }
}

```

