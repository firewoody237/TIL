> from **C# 프로그래밍 2판**

<br>

# C# 프로그래밍 첫걸음

C#은 `닷넷 플랫폼`을 활용하여 `모든 운영체제`에서 동작하는 프로그램을 만들 수 있다.

> `플랫폼`이란, 일반적으로 소프트웨어 응용 프로그램들을 실행하는 데 사용되는 하드웨어와 소프트웨어의 집합이다.

닷넷 플랫폼은 MS사가 만든 OS와 응용 프로그램의 `중간 레고블록`이다.

<br>

## 라이브러리와 프레임워크

닷넷 프레임워크는 `닷넷 플랫폼과 클래스 라이브러리가 합쳐진` 하나의 제품 이름이다.

### 라이브러리

특정 기능을 쉽게 사용할 수 있도록 `미리 만들어진` 코드

### 프레임워크

`제어의 역전`이 있는 `대규모 라이브러리`

프로그램의 초기화부터 종료까지의 `흐름을 직접 관리`함.

## C#으로 할 수 있는 일

- GUI 개발(Windows Form, WPF)
- 웹 개발(ASP.NET)
- 게임 개발
- IoT 개발

# 기본

## 기본 용어

### 표현식과 문장

`표현식`이 모여 `문장`, `문장`이 모여 `프로그램`을 만든다.

### 키워드

### 식별자

- 클래스, 속성, 메서드, 네임스페이스의 이름은 항상 `대문자로 시작`한다.
- 지역 변수와 전역 변수의 이름은 항상 `소문자로 시작`한다.
- `여러 단어`로 이루어진 식별자는 `각 단어의 첫 글자를 대문자`로 한다.

### 주석

<br>

## 출력

```c#
Console.WriteLine("Test");
```

<br>

## 기본 자료형

### 정수

- 정수끼리 연산했으면 정수가 결과로 나온다.

### 실수

### 문자

### 문자열

### 불

<br>

## 변수

### 정수 자료형

int, long

### 실수 자료형

float, double

### 문자 자료형

char

> `sizeof` 연산자를 활용하면 각 자료형의 크기를 알 수 있다.

### 문자열 자료형

string

### 불 자료형

bool

<br>

## 복합 대입 연산자

+=, -=, \*=, /=

<br>

## 증감 연산자

++, --

<br>

## 자료형 검사

> 프로그램 내부에서 자료형을 출력하고 싶은 경우 `GetType()` 메서드를 사용

<br>

## var 키워드

var 키워드의 조건

- `지역 변수`로 선언해야 함
- 변수를 `선언과 동시에 초기화` 해야 함

<br>

## 입력

```c#
Console.ReadLine()
```

<br>

## 자료형 변환

### 강제 자료형 변환

큰 자료형 -> 작은 자료형 : 데이터가 깨질 수 있음
`캐스팅` 사용 : (int)100.05

### 자동 자료형 변환

데이터 손실이 일어나지 않는 범위에 한해서 `자동으로 자료형을 변경`

### 다른 자료형을 숫자로 변환

```c#
int.Parse()
long.Parse()
float.Parse()
double.Parse()
```

### 다른 자료형을 문자열로 변환

```c#
.ToString()
```

### 다른 자료형들을 bool로 변환

```c#
bool.Parse()
```

<br><br>

# 조건문

## if 조건문

[코딩 가이드](https://docs.microsoft.com/ko-kr/dotnet/csharp/programming-guide/inside-a-progra/coding-conventions)

```c#
//if
if (condition1)
{
    sentence
}
else if (condition2)
{
    sentence
}
else
{
    sentence
}

//switch
switch (value)
{
    case value1:
        sentence
        break;
    default:
        sentence
        break;
}

//삼항 연산자
condition ? when_true : when false
```

<br>

# 반복문

```c#
//배열
int[] array = {1, 2, 3};
array.Length //3
int[] array1 = new int[100];

//while
while (condition)
{
    sentence
}

//do-while
do
{
    sentence
} while (condition)

//for
for (int i = 0; i < 반복 횟수; i++)
{
    sentence
}

//foreach
foreach (자료형 변수 in 컬렉션)
{
    sentence
}
```

## break 키워드

반복문 중간에 가장 `가까운` 반복문을 `종료`

## continue 키워드

반복문 중간에 이번 반복구절을 `넘어감`

<br><br>

# 클래스 기본

## 클래스 개요

### 사용자 정의 자료형

클래스 기반의 `객체 지향 언어`는 클래스라는 기능을 사용해서 우리가 원하는 `새로운 자료형`을 정의

### 클래스와 인스턴스

```c#
Car car = new Car();
//클래스 인스턴스 = new 생성자
```

<br>

## 클래스 사용

### Random 클래스

### List 클래스

가변적인 배열을 생성

클래스를 선언할 때 어떤 자료형인지를 알려주기 위해 제네릭을 사용

```c#
List<int> list = new List<int>();
```

### Math 클래스

> 클래스 이름 뒤에 점을 찍고 사용하는 멤버 : `클래스 멤버`

<br>

## 클래스 생성

```c#
class ClassName
{

}
```

### 하나의 파일에 여러 개의 클래스 생성

### 클래스 내부에 클래스 생성

### 서로 다른 파일에 클래스 생성

클래스는 파일 하나에 클래스 하나를 넣고, `파일의 이름과 맞추어` 만드는 것이 일반적이다.

> 클래스 파일을 빠르게 생성할 때 `Ctrl` + `.` 단축키 사용

<br>

## 클래스 변수

### 인스턴스 변수

C#은 인스턴스를 생성할 때 원하는 `변수를 원하는 값으로 초기화 하는 기능`이 있다.

```c#
class Program
{
    class Product
    {
        public string name;
    }

    static void Main(string[] args)
    {
        Product product = new Product() { name = "감자" };
    }
}
```

### 클래스 변수

클래스 변수를 만들 때는 `static`키워드를 사용한다.

<br>

## 추상화

프로그램에 사용되는 `핵심적인 부분`을 추출하는 것

> `모델 클래스` : 변수만 가지고 있는 클래스

> `partial` 클래스 : 클래스를 여러 곳에서 정의 가능

```c#
partial class Example
{
    public int a;
}

partial class Example
{
    public int b;
}
```

> `디스플레이 배율 문제` : 윈도우에서 모니터의 배율이 100%가 아닌 경우 'Scaling on your main display is set to 200%' 등의 메시지가 출력됩니다.

- 생성한 버튼을 화면에 붙이려면 화면의 `Controls` 속성을 사용한다.

<br><br>

# 메서드

## 메서드 기본 형태

<br>

## 매개변수와 반환

<br>

## 클래스 메서드

클래스 메서드는 `클래스명.메소드명`으로 사용한다.

`static` 키워드가 붙은 변수 or 메서드는 `프로그램을 실행하는 순간`에 `메모리`에 올라가게 된다. 클래스 메서드에는 아직 메모리에 올라가지 않은 인스턴스 변수와 인스턴스 메서드를 사용할 수 없다.

<br>

## 오버로딩

이름은 같고, 매개변수는 다른 메서드를 만드는 것을 `오버로딩`이라고 한다.

반환값이 다르다고 해서 오버로딩이 일어나지는 않는다.

<br>

## 접근 제한자

### private 접근 제한자

자신의 클래스 내부에 있는 클래스의 메서드나 자신의 클래스 내부에 있는 메서드에서만 접근 가능

### public 접근 제한자

<br>

## 생성자

인스턴스를 `생성할 때 자동으로 호출`되는 메서드

- `이름`은 클래스 이름과 같아야 한다.
- 접근 제한자는 `public`이어야 한다.
  - `private` 생성자는 아래와 같은 경우 사용한다.
    - `정적 멤버만` 가지고 있을 때
    - `팩토리 메서드 패턴`에서 팩토리 메서드로만 인스턴스를 생성하게 하고 싶을 때
- `반환`과 관련된 선언을 하지 않는다.

`정적 생성자`는 `정적 요소를 초기화할 때 사용`한다.

- `접근 제한자`를 사용하지 못한다.
- `매개변수`를 사용하지 못한다.
- 정적 요소를 사용할 때, 또는 인스턴스를 `생성하는 초기 시점`에 한 번만 호출

<br>

## 소멸자

`인스턴스가 소멸될 때에 호출`되는 소멸자가 있다. 변수가 더 이상 사용되지 않을 것이 확실할 때 객체를 소멸시키며 소멸자가 호출

- 이름은 클래스 이름 앞에 `~기호`가 붙는다.
- `접근 제한자`를 사용하지 않는다.
- `반환`과 관련된 선언을 하지 않는다.
- `매개변수와` 관련된 선언을 하지 않는다.
- 하나의 클래스에는 `하나의 소멸자`만 있을 수 있다.

웹 통신 종료 시 통신을 끊는 등에 사용한다.

> 상수는 자료형앞에 `const`를 붙여 만든다.

> 읽기 전용 변수는 자료형 앞에 `readonly`를 붙여 만든다.
>
> readonly는 변수를 선언하는 시점과 생성자 메서드에서만 값을 변경할 수 있다.

<br>

## 속성

### 캡슐화

### 겟터와 셋터

### 일반적인 속성 생성 방법

```c#
class Box
{
    private int width;
    public int Width
    {
        get { return width; }
        set
        {
            if (value > 0) { width = value; }
            else { Console.Write("!!"); }
        }
    }
}
```

속성 이름은 `대문자`로 시작하는 것이 C# 개발자들의 약속이다.

### 간단한 속성 생성 방법

```c#
public int Width { get; set; }
public int Height { get; set; }
```

> `속성 코드 조각` : `Ctrl` + `Space`

<br>

## 값 복사와 참조 복사

인스턴스를 생성하면 인스턴스는 `힙`이라는 영역에 위치를 잡는다.
이때에 주소 값이 변수에 들어간다.

<br><br>

# 상속과 다형성

## 상속과 다형성 소개

C#에서 반복을 줄이기 위해 `상속`과 `다형성`을 사용

<br>

## 상속

상속은 클래스 사이에 부모 자식 관계를 정의하는 작업

```c#
class Dog : Animal
```

자식 클래스는 부모 클래스의 `public` 또는 `protected` 멤버에 점근할 수 있음

부모의 메서드에 접근할 때 `base`키워드를 사용

<br>

## 다형성

하나의 클래스가 `여러 형태`로 변환될 수 있는 성질

부모로 위장한 자식은 부모의 멤버만 사용 가능

자식 클래스에 있는 메서드를 사용하려면, `자식 클래스로의 자료형 변환`을 해줘야 함

```c#
((Cat)item).Meow();
```

C#에서 만드는 모든 클래스는 Object라는 클래스의 상속을 받게 됨

<br>

## is 키워드

특정 클래스가 어떤 클래스인지 확인하기 위해 `is 키워드`를 사용

```c#
item is Dog
//객체 is 클래스
```

<br>

## 클래스 자료형 변환

### 일반적인 자료형 변환

(클래스) 변수

### as 키워드로 자료형 변환

변환에 실패하면 `null`을 반환

```c#
변수 as 클래스
```

<br>

## 상속의 생성자

자식 인스턴스를 생성하면, 부모가 가지고 있는 멤버 초기화를 위해 부모 생성자도 자동으로 호출

```c#
//명시적으로 사용하고 싶을 경우
public Child() : base()
```

- `클래스 변수`는 상속되어도 공유함

<br>

## 섀도잉과 하이딩

- `업스큐어링`이란 것도 있음

### 섀도잉

`섀도잉` : 특정한 영역에서 이름이 겹쳐서 다른 변수를 가리키는 것

### 하이딩

하이딩을 하게 되면 정상적인 상속을 막을 수 있음

`new`키워드를 사용

<br>

## 하이딩과 오버라이딩

`하이딩` : 부모 클래스와 자식 클래스에 동일한 이름으로 멤버를 만들 때 발생.

`하이딩`은 `멤버 전체`에서 일어나지만, `오버라이딩`은 `메서드`와 관련되어서만 일어남

## 오버라이딩

부모쪽엔 `virtual`, 자식쪽엔 `override사`용

```c#
class Parent
{
    public virtual void Method() {}
}

class Child : Parent
{
    public override void Method() {}
}
```

`하이딩`은 그냥 부모의 것을 실행하고 싶을 때 사용

<br>

## 상속과 오버라이딩 제한

### sealed 메서드

클래스에 적용하면 `절대 상속하지 말라`는 의미

메서드에 적용하면 `더 이상 오버라이딩하지 말라`는 의미

```c#
sealed class Parent {}

class Child
{
    sealed public override void Test() {}
}
```

### abstract 키워드

`무조건 상속`해서 쓰라는 의미

`abstract` 클래스 자체는 인스턴스를 만들 수 없음

`메소드`에 `abstract`를 적용하면 `클래스`에도 `abstract`를 적용해야 함

```c#
class Program
{
    abstract class Parent
    {
        public abstract void Test();
    }
}
```

`abstract` 키워드 자체가 반드시 오버라이딩 해야 하므로 `virtual` 키워드를 사용하지 않음

- 새로운 화면이 열려도 기존에 있던 화면을 조작할 수 있는 형태는 `모달리스`
- `MDI`는 하나의 화면 내부에 여러개의 다른 화면을 띄우는 것
- 새로운 화면을 띄웠을 때 기존의 화면을 조작할 수 없는 것은 `모달`

<br>

# 클래스 심화

## 제네릭

- 클래스 내부에서 `자료형에 별칭을 지정`하는 기능
- 보통은 식별자로 `T`를 사용
- `where` 키워드를 사용해서 제네릭 `타입을 제한`

```c#
class Wanted<T, U>
{
    where T : class //타입을 클래스로 제한
    where U : IComparable //타입을 IComparable 또는 자식으로 제한
}
```

<br>

## 인덱서

- 직접 만든 클래스에 `[]`를 사용

```c#
class Products
{
    public int this[int i]
    {
        get { return i; }
        set { Console.WriteLine(i); }
    }
}
```

<br>

## out 키워드

- `값을 여러개 반환`하고 싶을 때

```c#
class Program
{
    static void NextPosition(int x, int y, int vy, out int rx, out int ry)
    {
        rx = x + vx;
        ry = y + vy;
    }

    static void Main(string[] args)
    {
        int x = 0;
        int y = 0;
        int vx = 1;
        int vy = 1;

        NextPosition(x, y, vx, vy, out x, out y);
    }
}
```

<br>

## 구조체

- `간단한 객체`를 만들 때 사용
- `상속`이 불가능
- `인터페이스` 구현 불가능
- `안정성`이 높음
- 멤버 변수를 별도로 `초기화` 하지 않으면, 해당 멤버 변수 사용 시 오류 발생

```c#
class Program
{
    struct Point
    {
        public int x;
        public int y;
    }

    static void Main(string[] args)
    {
        Point point;
        point.x = 10;
        point.y = 10;
    }
}
```

<br>

### 구조체의 생성자

- `매개변수`가 없는 생성자 선언이 불가능(자동으로 정의되기 때문)
- 이 경우, 해당 자료형의 `기본 값`으로 초기화
- 매개변수를 다루는 생성자는 다음 제약이 생김
  - 모든 멤버 `변수를 초기화`된 상태로 만들어 줘야 함
  - 선언과 동시에 멤버 변수 초기화 불가능

<br>

### 구조체 복사

- 구조체는 `값 복사`가 이루어짐

```c#
class Program
{
    struct PointStruct
    {
        public int x;
        public int y;

        public PointStruct(int x, int y)
        {
            this.x = x;
            this.y = y;
        }
    }

    static void Main(string[] args)
    {
        PointStruct pointStructA = new PointStruct(10, 20);
        PointStruct pointStructB = pointStructA;

        pointStructB.x = 100;
        Console.WriteLint(pointStructA); //10;
    }
}
```
