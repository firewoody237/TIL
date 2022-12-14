> **<도서> 프로그래머의 뇌**
>
> 이 책의 목적은 우선 `두뇌가 코드를 처리하는 방식`을 이해하도록 돕는 것이다. 전문 프로그래머들은 새로운 정보를 접할 때가 많기 때문에, 새로운 정보가 제시될 때 `두뇌가 무엇을 하는지` 이해하면 `더 나은 프로그래머`가 되는 데 도움을 얻을 것이다.

<br>

프로그래밍에 있어서 `뇌`가 어떤식으로 개입할 수 있는지 안다면, 뇌를 잘 활용할 `초석`이 될 것이다.

<br>

각 장의 제목들은 내가 항상 고민해오고, 지금 업무에 있어서도 충분히 도움이 될만한 제목들이다.

<br>

책을 읽고나면, step-by-step으로 **꼭 실무에 적용 해 나아가자**.

<br>

---

## 목차

- [1. 코딩 중 겪는 혼란에 대한 이해](#1-코딩-중-겪는-혼란에-대한-이해)
  - [코드가 초래하는 세 가지 종류의 혼란](#코드가-초래하는-세-가지-종류의-혼란)
  - [코딩에 영향을 주는 인지 과정](#코딩에-영향을-주는-인지-과정)
- [2. 신속한 코드 분석](#2-신속한-코드-분석)
  - [코드를 신속하게 읽기](#코드를-신속하게-읽기)
  - [기억의 크기 제한을 극복하기](#기억의-크기-제한을-극복하기)
  - [읽는 것보다 보는 것이 더 많다.](#읽는-것보다-보는-것이-더-많다)
    - [1. 디자인 패턴의 사용](#1-디자인-패턴의-사용)
    - [2. 주석문 쓰기](#2-주석문-쓰기)
    - [3. 표식 남기기](#3-표식-남기기)
- [3. 프로그래밍 문법 빠르게 배우기](#3-프로그래밍-문법-빠르게-배우기)
  - [문법을 기억하기 위한 팁](#문법을-기억하기-위한-팁)
  - [플래시카드 사용해 문법 외우기](#플래시카드-사용해-문법-외우기)
  - [어떻게 하면 잊어버리지 않을 수 있을까?](#어떻게-하면-잊어버리지-않을-수-있을까)
  - [문법을 더 오랫동안 기억하기](#문법을-더-오랫동안-기억하기)
    - [인출](#인출)
    - [정교화](#정교화)
- [4. 복잡한 코드 읽는 방법](#4-복잡한-코드-읽는-방법)
  - [복잡한 코드를 이해하는 것이 왜 어려울까?](#복잡한-코드를-이해하는-것이-왜-어려울까)
  - [인지 부하를 줄이기 위한 기법](#인지-부하를-줄이기-위한-기법)
    - [인지적 리팩터링](#인지적-리팩터링)
    - [생소한 언어 구성요소를 다른 것으로 대치하기](#생소한-언어-구성요소를-다른-것으로-대치하기)
    - [플래시카드에 코드 동의어 추가](#플래시카드에-코드-동의어-추가)
  - [작업 기억 공간에 부하가 오면 쓸 수 있는 기억 보조 수단](#작업-기억-공간에-부하가-오면-쓸-수-있는-기억-보조-수단)
  - [의존 그래프](#의존-그래프)
  - [상태표 사용](#상태표-사용)
- [5. 코드를 더 깊이 있게 이해하기](#5-코드를-더-깊이-있게-이해하기)
  - [변수 역할 프레임워크](#변수-역할-프레임워크)
  - [역할과 패러다임](#역할과-패러다임)
  - [프로그램에 대해 깊이 있는 지식을 얻으려면](#프로그램에-대해-깊이-있는-지식을-얻으려면)
  - [텍스트를 읽는 것과 코드를 읽는 것은 유사하다](#텍스트를-읽는-것과-코드를-읽는-것은-유사하다)
  - [코드 읽기에 적용해볼 수 있는 텍스트 이해 전략](#코드-읽기에-적용해볼-수-있는-텍스트-이해-전략)

---

<br>

# 1. 코딩 중 겪는 혼란에 대한 이해

**다루는 내용**

1. 코딩 중에 혼란이 발생하는 `다양한 방식의 차이점` 이해
2. 코딩에서 작동하는 `세 가지 인지 과정`의 비교
3. 세 가지 인지 과정들이 어떻게 서로 `보완적`으로 작동하는지에 대한 이해

<br>

## 코드가 초래하는 세 가지 종류의 혼란

1. **지식의 부족** : 특정 키워드에 대한 지식이 없을 때
2. **정보의 부족** : 특정 로직이 내부적으로 어떻게 작동하는지 모를 때
3. **처리 능력의 부족** : 두뇌 처리 용량이 부족할 때

<br>

## 코딩에 영향을 주는 인지 과정

1. **장기 기억 공간(LTM)** - 지식
   1. 추상적인 알고리즘과 프로그래밍 언어의 문법을 기억하고, 나아가 키보드를 입력하는 동작을 기억하는 일을 함
2. **단기 기억 공간(STM)** - 정보
   1. STM 기억의 최대치는 보통 `12개`를 넘지 않는다.
   2. 코드에서 키워드, 변수명, 자료구조 등을 일시적으로 저장 함
   3. 함수의 역할을 파악하더라도, 한 시간후에 STM에서 지워질 수 있다.
3. **작업 기억 공간** - 처리 능력
   1. 실제 `사고 작용`이 일어남
   2. 매우 복잡한 프로그램을 트레이스할 때는 변수의 값을 코드 내에 혹은 별도로 적오놓고 싶은 마음이 들 수 있다. 이러한 현상은 작업 기억 공간이 꽉 차서 더 많은 정보를 처리할 수 없을 때 나타난다.

<br>

> 세 가지 인지 과정은 서로 `보완적으로 작동`한다.
> `STM`을 실행하면서 `LTM`을 참조하고, 결론적으로 `작업 기억 공간`에서 처리를 한다.

<br>

# 2. 신속한 코드 분석

**다루는 내용**

1. 경험 많은 개발자조차 코드를 `빨리 이해`하는 것이 어려운 이유
2. 두뇌가 정보들을 어떻게 `인식 가능한 부분`으로 나누는지에 대한 이해
3. 단어와 코드 같은 정보를 분석할 때 `LTM`과 `STM` 사이의 `상호작용`
4. 코드 분석 시 `영상 기억 공간`의 역할
5. 코드 기억을 통한 코딩 수준의 자가 진단
6. `읽기 쉬운 코드`를 작성하는 법

<br>

## 코드를 신속하게 읽기

- 프로그래머들은 `코드를 읽는 법`보다 `작성하는 법`을 훨씬 더 많이 연습한다. 하지만 `60%이상`을 코드를 읽는데에 시간을 사용한다.
- 여러 목적으로 코드를 읽지만, 한 가지 공통점은 코드를 읽을 때 우리는 그 코드에 존재하는 `특정한 정보`를 찾는다는 것이다.
- 코드를 읽으면, 코드에서 특정 부분에는 `LTM`을, 특정 부분에서는 `STM`을 활용하게된다.

<br>

1. 코드가 무슨일을 하는지 알지 못하면, `LTM`에 저장된 지식을 사용해서 추측하기 어렵다.
2. `생소한 변수명`을 사용하면 패턴을 찾고 기억하는 것이 어려워진다.

<br>

- STM은 꽤 작기 때문에, 이 작은 용량을 극복하기 위해 STM은 LTM과 `협업`하여 읽거나 기억한 정보를 이해한다.

<br>

## 기억의 크기 제한을 극복하기

- 밀러의 이론에 의하면 문자를 `6개`까지 읽고 나면 그 후 부터는 앞에 있었던 문자를 잊어버려야 한다.
- 이를 극복하기 위한 방법
  - 몇 개의 그룹으로 묶은 정보인 `Chunk`를 활용하는 방법.
  - 특정한 주제에 대해 두뇌가 더 많은 정보를 저장하고 있다면 입력된 정보들을 효율적으로 `청크로 묶는 것`이 수월해진다.
  - `LTM`에 지식이 많으면 기억을 쉽게 한다.

<br>

## 읽는 것보다 보는 것이 더 많다.

- 정보는 STM에 도달하기 전에 `감각 기억 공간`이라는 영역을 통과한다.
- 코드를 읽을 때는 감각 기억 공간중에 눈을 통해 저장되는 `영상 기억 공간`에 잠시 저장된다.
  - 눈을 감은 후에도 여전히 페이지의 모양을 볼 수 있는 것과 같은 것이다.
- 기억하는 대상이 중요한 것이 아니고, `기억하는 방식`이 중요하다.
- 일상적이고 예상 가능한 상황은 `청크`로 묶는 것을 쉽게 한다.

<br>

**청크로 묶을 수 있는 코드를 작성하는 방법**

### 1. 디자인 패턴의 사용

- 그룹으로 묶기 쉬운 코드를 작성하려면 `디자인 패턴`을 사용하면 된다. 디자인 패턴을 사용하는 것이 코드를 `유지 보수`하는 데 도움이 된다.

### 2. 주석문 쓰기

- 주석문은 코드를 읽는 시간을 더 길게만들지만, `개발자가 코드를 청킹하는 방식`에 영향을 미치므로 유의미하게 사용하면 순기능이 된다.

### 3. 표식 남기기

- 표식은 일반적으로 코드 내에서 사용하는 특정 자료구조, 알고리즘 혹은 접근 방식 등을 보여주는 라인이다. 표식은 코드를 읽고 이해하는 과정에서 소스 코드에 대해 개발자가 갖는 가정이 맞거나 틀린 것을 확인해주는 역할을 수행하기 때문에 매우 중요하다.

1. `단순 표식` : 의미 있는 변수명같이 코드의 문덥을 통해 의미가 자명한 표식(ex. root, tree)
2. `복합 표식` : 단순 표식들이 모여 함께 실행하는 기능에 대해 알려 줌

`숙련된 개발자`일수록 표식을 잘 이용한다.

**표식 찾기 연습**

1. `코드 선정`
   1. 잘 알지 못하는 코드베이스를 선택하되 자신이 잘 아는 언어로 된 코드를 선정한다. 가능하다면 지인이 그 코드베이스를 자세히 알고 있으면 좋다. 그럼 자신이 이해한 것이 맞는지 그 사람을 통해 확인받을 수 있다. 이제 선정한 코드베이스에서 메서드나 함수 하나를 선택한다.
2. `코드 파악`
   1. 1단계에서 선택한 메서드나 함수를 파악하고 코드가 하는 일을 요약해보라.
3. `사용하는 표식의 적극적 확인`
   1. 읽는 도중 '아, 그렇구나'라는 생각이 들면서 그 코드의 의미를 좀 더 이해하게 되면 잠시 멈추고 왜 그렇게 생각했는지를 적어보라. 주석문, 변수명, 메서드명, 임시 저장값 등 어느 것이든 표식이 될 수 있다.
4. `회고`
   1. 코드를 충분히 이해하고 표식을 나열했으면 이제 다음 질문들에 대해 답해보자.
      1. 어떤 표식을 찾았는가?
      2. 찾은 표식들은 코드의 요소인가, 아니면 사람의 언어로 된 정보인가?
      3. 그 표식들은 무엇에 관해 알려주고 있는가?
      4. 그 표식들은 코드의 도메인에 대한 지식을 나타내는가?
      5. 그 표식들은 코드의 기능에 대한 지식을 나타내는가?
5. `코드에 다시 적용`
   1. 가능하다면, 새로 표식을 추가하거나 기존의 표식을 추가해서 더 개선 해 보라
6. `다른 사람과 비교`

<br>

**청킹 연습**

1. `코드 선정`
   1. 위와 동일하게, 코드가 50줄을 넘지 않도록 한다.
2. `코드 파악`
   1. 최대 2분을 넘지 않도록 타이머를 설정하고 코드를 파악한다.
3. `코드 재현`
   1. 종이 혹은 IDE에 기억을 되살려 다시 작성해 본다.
4. `회고`
   1. 작성한 코드를 원래 코드와 비교해보고 다음 질문에 답해본다.
      1. 어느 부분을 쉽게 기억했는가?
      2. 부분적으로 기억한 코드가 있는가?
      3. 전체를 다 기억하지 못한 코드가 있는가?
      4. 기억하지 못한 라인들이 있다면 그 이유가 무엇일까?
      5. 기억하지 못한 라인에 본인이 익숙하지 않은 프로그래밍 개념이 들어 있지는 않은가?
      6. 기억하지 못한 라인에 본인이 익숙하지 않은 도메인 지식이 있지는 않은가?
5. `다른 사람과 비교`

<br>

- `LTM 지식`이 부족하면 코드를 읽을 떄 `하위 수준의 정보`들 이를테면 문자나 키워드 같은 것에 의존해야 한다. 이럴 때 `STM`의 공간이 빠르게 소진된다.
  - 평소에 공부해서 `LTM의 지식`을 늘려야 한다.
- `LTM`이 코드와 관련 있는 지식을 충분히 가지고 있다면 코드의 하위 수준의 요소들을 STM에 저장하는 대신 `추상적인 개념`을 기억하기 때문에 `STM`의 공간을 절약한다.

<br>

# 3. 프로그래밍 문법 빠르게 배우기

**다루는 내용**

1. 프로그래밍 언어 문법에 대한 `폭넓은 지식`이 중요한 이유의 고찰
2. 프로그래밍 언어 문법을 기억하기 위한 `방법`의 선택
3. 문법을 잊어버리지 않기 위해 할 수 있는 방법
4. 문법과 개념을 언제 공부하면 가장 큰 효과를 볼 수 잇는지에 대한 유추
5. 문법과 프로그래밍에 대한 개념이 `어떻게 LTM에 저장되는지`에 대한 이해
6. 프로그래밍 개념을 좀 더 잘 기억할 수 있기 위한 `정교화 학습`

<br>

> **2장에서 배운 점**
>
> 코드를 효율적으로 이해하는 정도는 `이미 알고 있는 지식`에 의해 영향을 받는다. 따라서 프로그래밍 언어의 문법, 개념과 자료구조를 외우면 코드를 더 빨리 파악하는데 도움이 된다.
>
> **그렇다면, 어떻게 빠르게 외울 수 있을까?**

<br>

## 문법을 기억하기 위한 팁

- `코드를 기억하는 것`이 왜 중요한가?
  - 개념, 자료구조, 문법을 더 많이 알수록 두뇌는 더 많은 `코드를 쉽게 분리`하고 `기억하고 처리`할 수 있다.
  - 두뇌가 작업을 하다가 `업무 중단`(코드를 찾아보는 등)을 받게 되면, 생산성에 악영향을 미친다. 중단을 다시 업무로 돌아가기까지 보통 `15분`이 소요된다.
  - 작업했던 내용을 잊어버리는 바람에 그것을 기억하기 위해 의도적으로 노력해야 했다.

<br>

## 플래시카드 사용해 문법 외우기

**앞면에 개념을 적어놓고 뒷면에 해당하는 코드를 적는다.**
**문법을 다른 종이에 적거나 에디터에서 입력한 다음 카드를 뒤집어 맞았는지 확인한다.**

<br>

- `세레고`, `안키`, `퀴즈렛` 같은 앱을 사용하면 좋다.

- 플래시카드를 작성하기 좋은 때
  - `새로운 개념`을 접했을 때
  - 어떤 개념을 `검색`할 때
- 어떤 내용을 플래시카드로 만들지는 스스로 판단할 수 있어야 한다.
- 모든 문법을 다 암기할 필요는 없다.
- 플래시카드 개수를 줄여나간다.

<br>

## 어떻게 하면 잊어버리지 않을 수 있을까?

- LTM에도 영원히 저장되는 것은 아니다. LTM에 저장된 정보가 없어지는 것은 생각보다 훨신 짧다
- 두뇌의 기억은 `네트워크 구조`로 되어있다. 하나의 사실은 다른 많은 사실과 `연결`되어 있다.
- 긴 간격을 두고 공부한 그룹의 기억하는 비율이 현저히 높다.
  - = 오랫동안 학습한 만큼 더 오래 기억한다.
  - = 더 오랜 간격을 두고 학습해야 한다.
- 플래시카드를 `한달에 한 번 다시 학습`하면 오랫동안 기억하는 데 충분하다.

<br>

## 문법을 더 오랫동안 기억하기

**기억을 강화하는 두 가지 테크닉**

1. `인출` : 적극적으로 무언가를 일부러 기억해보려고 애씀
2. `정교화` : 기존 기억에 새로운 지식을 적극적으로 연결시킴

<br>

### 인출

**정보를 기억하는 두 가지 형태**

1. `저장강도` : 무언가를 LTM에 얼마나 잘 저장하고 있는가
2. `인출강도` : 무언가를 얼마나 쉽게 기억할 수 있는가

<br>

- 답이 입에서 맴돌기만 하고 기억이 나지 않았던 경험은, 정보에 대해 저장 강도는 높지만 인출 강도는 낮다는 것이다.
- 저장 강도는 감소하지 않고 늘어나지만, 인출 강도는 시간이 흐를수록 약해진다.
- 자기가 이미 알고 있다고 생각하는 내용을 기억하려고 노력하면 추가 학습 없이도 인출 강도가 강화된다.
- 학습을 추가로 하지 않고 정보를 기억하려고 `능동적으로 노력`하는 것만으로도 배운 것을 많이 기억할 수 있다.
- 너무 쉽게 정보를 찾고 또 그것이 너무 일상적으로 이뤄지다 보니 우리 두뇌는 문법을 기억할 필요가 없다고 느낀다. 따라서 프로그래밍 문법에 대한 인출 강도가 강화되지 않고 계속 약한 상태로 남아 있게 된다.

<br>

### 정교화

- `정교화`는 복잡한 프로그래밍 개념을 학습할 때 효과가 좋다.
- 새로운 정보를 학습할 때 정보는 LTM에 저장하기 전에 먼저 `스키마`(사고나 생각이 서로 관련되어 조직된 방식)의 형태로 만들어진다. 이미 존재하는 스키마에 잘 맞는 정보일수록 더 쉽게 기억할 수 있다.
- 인출 강도는 다른 기억에 연관된 기억일 때 더 높다.

<br>

**정교화와 새로운 기억을 강화하는데 도움이 되는, 새로운 프로그래밍 개념을 배울 때의 연습**

- 새로운 개념이 어떤 다른 개념을 생각나게 했는가? 모든 관련된 개념을 적어보라.
- 위에서 적은 관련된 개념에 대해 다음 질문들에 답해보라.
  - 새로운 개념은 왜 이미 알고 있는 그 개념을 생각나게 했을까?
  - 문법에 공통적인 점이 있는가?
  - 비슷한 환경에서 사용될 수 있는가?
  - 이 새로운 개념은 이미 알고있는 그 개념 대신 사용될 수 있는가?
  - 동일한 목적을 달성하기 위해 작성할 수 있는 다른 방법의 코드를 알고 있는가? 같은 결과를 갖는 비슷한 코드를 최대한 많이 만들어보라.
  - 다른 프로그래밍 언어에서는 같은 개념이 있는가? 비슷한 동작을 수행하는 다른 언어의 예제 코드를 작성할 수 있는가? 그것들은 서로 어떻게 다른가?
  - 이 개념은 어떤 패러다임, 도메인, 라이브러리 혹은 프레임워크와 잘 맞는가?

<br>

# 4. 복잡한 코드 읽는 방법

<br>

**다루는 내용**

1. 작업 기억 공간이 복잡한 코드에 의해 `과부하`가 걸릴 때 어떤 일이 일어나는지 분석
2. 프로그래밍에서 두 가지 종류의 작업 기억 공간 과부하
3. 과부하가 걸린 작업 기억 공간을 보상하기 위해 읽기 쉬운 코드로 `리팩터링`하는 법
4. 복잡한 코드를 읽을 때 작업 기억 공간을 지원하기 위해 `상태표`와 `의존 그래프` 작성하기

<br>

- 때론 코드가 너무 복잡해서 많은 문법지식과 효율적인 청킹으로도 코드를 이해하기 어려울 때가 있다.

<br>

## 복잡한 코드를 이해하는 것이 왜 어려울까?

- `STM`의 역할이 `정보를 기억`하는 것인 반면, `작업 기억 공간`의 역할은 `정보를 처리`하는 것이다.
- 작업 기억 공간도 한 번에 `2개에서 6개`까지만 기억할 수 있다.
- 이 용량을 `인지부하` 라고 한다.

1. `내재적 부하`
   1. `그 자체가 갖는 특성` 때문에 발생하는 인지 부하
   2. 내제된 문제에 대한 내용
2. `외재적 부하`
   1. 내재적인 부하에 `더해서` 문제에 추가되는 인지 부하
   2. 구현 방식등에 대한 내용
3. `본유적 부하`

- 익숙하지 않은 코드를 읽을 때 내재적 `인지 부해 / 외제적 인지 부하`로 `구분`해 보는 것도 도움이 된다.

<br>

## 인지 부하를 줄이기 위한 기법

<br>

### 인지적 리팩터링

- 유지보수를 위한 리팩터링이 아닌, 기능은 유지한채 '나에게 있어서' `가독성이 높은 코드로` 코드의 내부 구조를 개선한다.
- 메서드 이름이 `모호`하면 메서드의 기능을 이해하느라 시간이 소요되고 그런 일이 여러 번 반복된 다음에야 그 메서드의 기능이 LTM에 저장된다.
- 코드 내에서 `메서드의 순서`를 변경하는 것도 도움이 된다.

<br>

### 생소한 언어 구성요소를 다른 것으로 대치하기

- 코드에 있는 프로그래밍 개념이 익숙하지 않을 경우
- 익숙하지 않은 언어 구성 요소는 작업 기억 공간에 외재적 인지 부하를 늘리기 때문에 복잡한 코드를 읽을 때는 이들로 인한 부하가 늘어나지 않게 하는 것이 좋다.
- 생소한 구성요소를 같은 기능을 하지만 `다른 쉬운 방법`으로 구현해라

<br>

### 플래시카드에 코드 동의어 추가

<br>

## 작업 기억 공간에 부하가 오면 쓸 수 있는 기억 보조 수단

<br>

**복잡한 구조의 코드가 유발하는 과부하**

1. 정확히 코드의 어디를 `파악`해야 하는지 모를 때
2. 코드가 `서로 밀접하게 연결`되어 있는 경우 두뇌는 두 가지 작업을 동시에 수행

<br>

## 의존 그래프

흐름을 이해하고 `논리적 흐름`에 따라 코드를 읽는 데 도움이 되는 것

<br>

1. 모든 변수를 원으로 표시(한 가지 색으로)
2. 비슷한 변수를 연결
3. 모든 메서드나 함수 호출을 원으로 표시(변수와 다른 색으로)
4. 메서드나 함수 호출을 정의와 연결
5. 클래스의 모든 인스턴스를 원으로 표시
6. 클래스와 그 클래스의 인스턴스를 연결

<br>

## 상태표 사용

`변수`에 중점을 둠

1. 모든 변수를 나열한다
2. 테이블을 만들고 각 열에 하나의 변수를 기입한다.
3. 코드의 실행 단계마다 행을 만든다.
4. 코드를 각 단계별로 실행하고 그 단계에서 변수들의 값을 해당하는 열과 행에 적는다
   1. 특정 변수만 추적하고, 특정 변수만 생략하면 안된다.

<br>

**예제1**

```java
public class Calculations {
    public static void main(String[] args) {
        char[] chars = {'a', 'b', 'c', 'd'};
         // bba를 찾는다
         calculate(chars, 3, i -> i[0] == 1 && i[1] == 1 && i[2] == 0);
        }

    static void calculate(char[] a, int k, Predicate<int[]> decider) {
        int n = a.length;
        if (k < 1 || k > n) t
        hrow new IllegalArgumentException("Forbidden");

        int[] indexes = new int[n];
        int total = (int) Math.pow(n, k);

        while (total-- > 0) {
            for (int i = 0; i < n - (n - k); i++)
                System.out.print(a[indexes[i]]);
            System.out.println();

            if (decider.test(indexes))
                break;

            for (int i = 0; i < n; i++) {
                if (indexes[i] >= n - 1) {
                    indexes[i] = 0;
                } else {
                    indexes[i]++;
                    break;
                }
            }
        }
    }
}
```

**예제2**

```java
public class App {
    private static final int WIDTH = 81;
    private static final int HEIGHT = 5;
    private static char[][] lines;
    static {
        lines = new char[HEIGHT][WIDTH];
        for (int i = 0; i < HEIGHT; i++) {
            for (int j = 0; j < WIDTH; j++) {
                lines[i][j] = '*';
            }
        }
    }
    private static void show(int start, int len, int index) {
        int seg = len / 3;
        if (seg == 0) return;
        for (int i = index; i < HEIGHT; i++) {
            for (int j = start + seg; j < start + seg * 2; j++) {
                lines[i][j] = ' ';
            }
        }
        show(start, seg, index + 1);
        show(start + seg * 2, seg, index + 1);
    }

    public static void main(String[] args) {
        show(0, WIDTH, 1);
        for (int i = 0; i < HEIGHT; i++) {
            for (int j = 0; j < WIDTH; j++) {
                System.out.print(lines[i][j]);
            }
            System.out.println();
        }
    }
}
```

<br>

# 5. 코드를 더 깊이 있게 이해하기

<br>

**다룰 내용**
1. 변수가 프로그램에서 수행하는 여러 가지 `역할`
2. 코드의 `표면적 지식`과 코드 `작성자의 의도`를 이해나는 것의 비교
3. `인간의 언어와 프로그래밍 언어`를 읽고 이해하는 것의 비교
4. 코드를 깊이 있게 이해하기 위한 다양한 전략

<br>

> 코드가 하는 일이 무엇인지 이해하고 나면, 다음 단계는 코드에 대해 좀 더 깊이 생각하는 것이다. 코드는 어떻게 작성되었고 새로운 기능은 어디에 추가해야 하며 다른 방식으로 설계를 한다면 어떤 것이 가능할까?

<br>

## 변수 역할 프레임워크

`적절한 변수명`은 `표식`으로 사용될 수 있고 읽고 있는 코드를 `깊이 이해`하는 데도 도움이 된다.

<br>

**변수의 11가지 역할** - 변수 역할 프레임워크
1. `고정값` : 초기화를 통해 값이 할당된 이후 값이 변경되지 않는 변수
2. `스테퍼` : 루프를 반복 실행하며 값이 단계적으로 변하는 변수
3. `플래그` : 무엇인가 발생했거나 어떤 경우에 해당하는지를 나타내는 변수
4. `워커` : 자료구조를 순회
5. `최근값 보유자` : 어떤 값이 변해갈 때 가장 최근에 변경된 값을 갖는 변수
6. `목적값 보유자` : 찾고자 하는 값 혹은 현재까지 발견된 값 중에서 찾고자 하는 조건에 부합하는 값을 갖는 변수
7. `모집자` : 데이터를 모으거나 모은 데이터에 대해 어떤 연산을 수행하여 얻은 값을 저장하는 변수
8. `컨테이너` : 값을 새로 추가하거나 삭제할 수 있는 자료구조
9. `추적자` : 알고리즘에서 이전 값 혹은 다음 값을 추적하는 변수
10. `조직자` : 다른 값을 저장하기 위한 목적으로 사용하는 변수
11. `조직자` : 잠시만 사용하기 위한 변수

<br>

## 역할과 패러다임

`변수 프레임워크` - 변수의 이름 / 변수의 타입 / 변수의 역할이 이루어지는 연산 / 변수의 역할 을 구분하는 작업을 자주 해보라

<br>

## 프로그램에 대해 깊이 있는 지식을 얻으려면

프로그래머가 소스 코드를 이해하는 두 개의 서로 다른 층위에 대한 모델

1. `텍스트 구조 지식` : 키워드가 하는 일이나 변수의 역할 같은 `프로그램의 표면적인 이해`와 관련있음
2. `계획 지식` : 프로그래머가 프로그램을 작성할 때 `계획한 것`이 무엇인지 혹은 `무엇을 달성`하려고 했는지

<br>

프로그래머는 어디서 부터 읽기 시작해야 할지 알아야 한다.
1. **초점을 찾는다.**
   1. 하나의 `초점`에서 코드 파악을 시작한다.
   2. 깊은 이해가 필요한 코드
2. **초점으로부터 지식을 확장한다.**
   1. 코드에 존재하는 관계를 초점에서부터 찾아본다.
   2. 하이라이트한 코드인 `슬라이스`를 집중해서 살펴보면 프로그램의 어디에서 데이터가 사용되는지 이해하는 데 도움이 된다.
3. **관련된 개체로부터 개념을 이해한다.**
   1. 중요한 부분을 파악하고 나면 모든 관련 클래스를 나열한다.
   2. 이들의 관계를 적어놓고 그것에 대해 깊이 있게 생각해보라
4. **여러 개체에 걸쳐 있는 개념을 이해한다.**
   1. 코드에 있는 자료구조 뿐만 아니라 해당 자료구조에 적용된 연산과 그 연산에 대한 제약도 이해한다.

<br>

## 텍스트를 읽는 것과 코드를 읽는 것은 유사하다

> 연습의 부족, 좋은 전략과 훌륭한 스키마의 부재 등으로 개발자들은 코드를 한 줄 한 줄 읽거나 디버거로 코드를 라인 단위로 실행시키곤 하는데 이런 방식은 시간이 많이 소요된다.
> 
> 이로 인해 기존 코드를 파악해서 재사용하거나 수정하기보다는 자신이 코드를 처음부터 다시 작성하는 것을 선호하는 상황으로 이어진다.

<br> 

* `프로그램을 읽을때`와 `인간의 언어로 된 텍스트`를 읽을 때 비슷한 뇌를 사용한다.
* `언어 능력`이 가장 많은 영향을 미친다.
* 초급 프로그래머는 텍스트와 코드를 읽을 때 움직임의 80%정도는 `순차적`이였다.

## 코드 읽기에 적용해볼 수 있는 텍스트 이해 전략
1. **활성화**
   1. 코드를 스캔하여 코드 내에 존재하는 개념과 문법적 요소들에 대한 일차적인 이해를 한다.
2. **모니터링**
   1. 무엇이 이해되고, 무엇이 이해되지 않는지 확실하게 표기하여 구분한다.
3. **중요도 결정**
   1. 코드의 어느 부분이 가장 중요한 영향을 끼치는지에 대해 생각해본다.
4. **추론**
   1. 코드가 어떤일을 수행하는지 전혀 알 수 없을 때에도 의식적으로 변수에 주목한다.
   2. 변수명은 중요한 표식이다.
5. **시각화**
   1. 상태표를 작성하거나 코드 흐름을 추적하는 등의 시각화를 한다.
6. **질문**
   1. 스스로에게 질문한다.
7. **요약**
   1. 코드를 우리가 사용하는 언어로 요약한다.


<br>