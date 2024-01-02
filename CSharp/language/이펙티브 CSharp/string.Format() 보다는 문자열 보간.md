# Item 1. string.Format()을 보간 문자열로 대체하라.
> Chapter 1. 언어 요소

- 문자열 보간은 C# 6.0에 새롭게 도입되었다.
- 컴파일러 입장에서는 정적 타입 검사를 수행할 수 있기 때문에 개발자의 실수를 미연에 방지할 수 있고, 코드 가독성이 향상된다.

- `string.Format()`은 직접 실행하기 전까지는 짐작하기 어렵다.
- 인자의 개수가 정확히 일치하는지 확인하지 않는다.

- 보간 문자열은 문자열 앞에 `$`를 붙이면 된다.

```c#
Console.WriteLine($"The value of pi is {Math.PI}");
```

 - 위코드에서 `Math.PI`는 `double`이므로 값 타입이다. 따라서 이를 `object` 타입으로 변경하려면 박싱을 수행해야 한다.
 - 박싱을 수행해야 하므로, 너무 자주 사용하면 성능에 영향을 미칠 수 있다.

```C#
Console.WriteLine($"The value of pi is {Math.PI.ToString()}");
```

- 위 코드와 같이 피할 수 있다.

```C#
Console.WriteLine($"The value of pi is {Math.PI.ToString("F2")}");
Console.WriteLine($"The value of pi is {Math.PI:F2}");
```

- 추가적인 인자를 전달하여 포매팅을 표현할 수 있다.

```C#
Console.WriteLine($"The value of pi is {round ? Math.PI.ToString() : Math.PI.ToString("F2")}); // 컴파일 오류

Console.WriteLine($@"The value of pi is {(round ? Math.PI.ToString() : Math.PI.ToString("F2"))}); //성공
```

- C#은 `:`을 포맷 문자열의 시작을 나타내는 것으로 판단한다.

```C#
string result = default(string);
Console.WriteLine($@"Record is {(records.TryGetValue(index, out result) ? result : $"No record found at index {index}")}");
```

- 보간 문자열 내 다른 보간 문자열을 포함시킬 수도 있다.

```C#
var output = $@"The First five items are: {src.Take(5).Select(n => $@"Item: {n.ToString()}").Aggregate((c, a) => $@"{c}{Environment.NewLine}{a}")}";
```

- LINQ 구문과 문자열 보간 기능을 함께 쓸 수도 있다.

</br>

- 어떤 경우라도 문자열 보간 기능의 결과가 문자열이라는 사실을 잊어서는 안 된다.
- 모든 값이 대체되고나면 단일의 문자열만이 남을 뿐이다.
- 이런 사실은 SQL 쿼리문을 생성하는 경우에 간혹 혼동을 일으키기도 한다.
- 이 때문에 SQL 명령을 만들 때 문자열 보간 기능을 사용하는 것은 그리 추천할 만한 방식이 아니다.
- 나중에 객체나 데이터로 재해석이 필요한 문자열을 생성해야 하는 경우라면 문자열 보간 기능을 사용할 때 각별히 주의해야 한다.

</br>

- 기존 방식은 오류를 유발할 가능성도 높고, 문자열 보간 기능은 실수를 줄일 수 있고 더욱 강력할 뿐 아니라 활용도 또한 매우 높은 기술이다.
