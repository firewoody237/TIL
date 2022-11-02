# 싱글톤 패턴

> `단 하나`만 존재하는 객체 인스턴스를 공유하여 사용하는 패턴

일반적으로 객체를 사용할 때, 변수에 새로운 인스턴스를 만들어 사용한다.

```java
Class Cat { ... }

//...

Cat arong = new Cat();
Cat darong = new Cat();
```

<br>

객체의 경우 생성될 때마다 메모리 영역인 `힙`에 할당된다.

인스턴스가 한두개면 괜찮겠지만, `여러 트래픽`에서 객체를 생성한다면 힙 영역이 부족하게 될 수도 있다.

객체마다 비슷한 동작을 하는데, 매번 객체를 생성하는 것도 메모리에 있어서 비효율적이다.

이를 위해, 객체를 한번만 생성하고 필요한 곳에서 생성되어 있는 `한 객체(Single)를 사용하는 것`을 `싱글톤 패턴`이라고 한다.

<br>

```java
Class Cat{
    private static Cat instance;

    private Cat() { }

    public static Cat getInstance() {
        if(instance == null){
            instance = new Cat();
        }
        return instance;
    }
}

//...

Cat arong = Cat.getInstance();
Cat darong = Cat.getInstance();

arong == darong //true
```

소스와 같이 Cat의 인스턴스를 여기저기서 생성할 수 없도록 `private` 접근 제한을 걸고,

그리고 `getInstance`로 항상 같은 객체를 사용하는 방법으로 싱글톤 패턴을 사용한다.
