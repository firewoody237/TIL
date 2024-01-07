# Item 1. 지역변수를 선언할 때는 var를 사용하는 것이 낫다.
> Chapter 1. 언어 요소

- `C#`은 익명 타입을 지원하기 위해서 타입을 암시적으로 선언할 수 있는 방법을 제공한다.
- 정확한 반환 타입을 알지 못한 채 올바르지 않은 타입을 명시적으로 지정하면, 득보다 실이 많다.
- 정확한 타입을 기술하기 보다는, 타입을 유추할 수 있는 **좋은 변수이름**이 더 좋다.
- 좋은 변수이름과 `var`를 사용하면, 개발자는 **변수의 의미 파악**에 더 집중할 수 있다.
- 지역변수에 대한 타입 추론이 `C#`의 고유 특성인 `Static Typing`을 훼손하는 것은 아니다.
- `C#`에서 특정 변수를 `var`로 선언하면 동적 타이핑이 수행되는 것이 아니라, 할당 연산자의 오른쪽 타입을 확인하여 왼쪽 변수의 타입을 결정한다.

</br>

## 가독성 문제를 유발하는 케이스들
- (Bad) 메서드 이름만으로 짐작하기 어려운 경우

```c#
var result = someObject.DoSomeWork(anotherParameter);
```

- (Good) 타입을 쉽게 유추할 수 있는 경우

```c#
var foo = new MyType();
```

- (Good) 팩토리 메서드를 사용하는 경우

```c#
var thing = AccountFactory.CreateSavingAccount();
```

- (Good) 변수 이름을 통해 타입이 유추되는 경우

```c#
var HighestSellingProduct = someObject.DoSomeWork(anotherParameter);
```

</br>

---

</br>

- 현재의 `C#` 컴파일러는 런타임에 객체가 어떤 타입이 될지를 추론할 만큼 훌륭하지 않아서, 단순히 컴파일타임 타입과 메서드의 원형을 기반으로 변수의 타입을 추론할 뿐이다.
- 가끔은 개발자가 짐작한 타입과 컴파일러가 실제로 추론한 타입이 달라서 문제가 되는 경우도 있다. 이로 인해 미묘한 버그가 발생할 수 있으며 이 경우 코드 수정이 쉽지 않다.

</br>

---

</br>

- 아래와 같이 숫자를 사용할 때, 숫자 타입에 따라 `total`의 타입이 매우 다양해진다.
- 따라서, 내장된 숫자 타입과 `var`를 함께 사용할 때는 항상 주의해야 한다.
- 숫자 타입(int, float, double 등)은 명시적으로 타입을 선언하는 것이 좋다.

```c#
var f = GetMagicNumber();
var total = 100 * f / 6;
```

- `total`을 명시적으로 선언하면 좋다.

```c#
var f = GetMagicNumber();
double total = 100 * f / 6;
```

</br>

---

</br>

- 컴파일러는 일관된 방식으로 타입 추론을 수행하겠지만, 개발자 입장에서는 내부적으로 이뤄지는 타입 추론 과정과 암시적 변환 과정을 쉽사리 이해하기 어렵기 때문에 `var`을 사용함으로써 코드의 유지보수가 더 어려워 지기도 한다.
- 아래 코드는 심각한 성능문제를 유발한다.
  - `IEnumerable<String>`를 사용하게 되면, `q`를 조회하며 쿼리를 수행하고, `q2`를 조회하며 쿼리를 `q`에서 다시 수행한다.


```c#
public IEnumerable<string> FindCustomersStartingWith1(string start)
{
    IEnumerable<string> q = from c in db.Customers
                            select c.ContactName;

    var q2 = q.Where(s => s.StartsWith(start));
    return q2;
}
```

- 아래 코드는 성능 문제를 해결한다.
  - `IQueryable<T>`를 사용하면, `q`와 `q2` 쿼리들을 합한 후 한번에 수행한다.

```c#
public IEnumerable<string> FindCustomersStartingWith1(string start)
{
    var q = from c in db.Customers
            select c.ContactName; //IQuiryable로 자동 추론

    var q2 = q.Where(s => s.StartsWith(start));
    return q2;
}
```

</br>

---

</br>

- **확장 메서드**는 `virtual`로 선언될 수 없으므로 객체의 런타임 타입에 따라 다르게 동작하도록 작성할 수 없다. 또한 확장 메서드는 반드시 `static`으로 선언해야 한다.
- 이 때문에 컴파일러는 객체의 런타임 타입이 아니라 컴파일타임 타입에 준하여 메서드를 수행한다.
- 확장 메서드를 작성할 때 매개변수의 런타임 타입을 검사하여 서로 다르게 동작하도록 만들 수는 있다.
  - `Enumerable.Reverse()`는 매개변수가 `IList<T>`이거나 `ICollection<T>`일 경우 성능을 개선하기 위하여 런타임 타입 확인 기법을 활용한다.
- 코드를 읽을 때 지역변수의 타입을 명확히 유추할 수 없고 모호함을 불러일으킬 가능성이 있다면 차라리 타입을 명시적으로 선언하는 것이 좋다.
- 하지만 대부분의 경우 변수의 이름을 통해 역할을 명확히 드러내도록 작성하는 것이 좋다.
