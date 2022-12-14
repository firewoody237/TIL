### 들어가기 전

<br>

`CNCF(Cloud Native Computing Foundation)`은 클라우드 네이티브를 구성하는 기술 요소 세가지를 발표했다.
`컨테이너` 및 `오케스트레이션`이 **인프라**를 혁신했다면, `마이크로 서비스`는 **애플리케이션**의 혁신을 주도하고 있다.

<br>

1. `컨테이너`
2. `컨테이너 오케스트레이션`
3. `마이크로서비스`

<br>

# 1부. 마이크로서비스의 아키텍처

## 1장. 디지털 전환 : 마이크로서비스가 중요해진 배경

### 디지털 전환이란?

- `디지털 전환(DT or DX)`은 사람이 수작업으로 하던 프로세스를 디지털화된 프로세스로 변경하거나 오래된 디지털 기술을 최신 기술로 변경하여, 서비스나 프로세스를 혁신하는 디지털 기술의 적용 형태다.
- DX에 있어 디지털 솔루션은 단순히 지금까지 방법을 개선하거나 효율적으로 지원하는 것이 아니다. 자동화에 그치지 않고 `새로운 종류의 혁신과 창조성`을 만들어내는 것이다.
- `대부분의 일반 기업`에서는 IT는 주판이나 계산기처럼 `비즈니스를 지원하는 도구`이며, 비즈니스 주체는 어디까지나 사업 부서의 인력이었다.
- DX는 이런 기존 IT 비즈니스 협업 모델을 근본적으로 바꾸는 것이다. DX 이후의 세계에서 IT 시스템은 후방 지원 서비스가 아니다. **IT 시스템은 시장에 상품 및 서비스를 제공하며, 비즈니스 프로세스를 운영하는 기업 활동의 핵심이 된다.**

<br>

### 2025년의 벽

- 자주 기존 IT 시스템을 업데이트 하는 것이 기존 제품/기술과 최신 제품/기술의 차이를 줄여서 현재 이용하고 있는 제품/기술 간의 전환이 쉽도록 해주며, 개발, 구축, 운영 관련된 IT 기술자도 기술을 손쉽게 향상시킬 수 있다.
- `기술적 부채`가 많아지면 운영해야 할 제품/기술이 늘어나고 IT 기술자의 기술 향상 부담도 늘어나서 IT 시스템 현대화 시에 기간이나 비용적 부담이 커진다.

<br>

- `DX 실현`을 위한 네 가지 주요 해결 방침

1. `IT 인프라 표준화`
   1. 최신 기술을 사용해서 인프라 표준화를 도모하고 환경 구축, 운영의 효율화와 속도 향상을 목표
   2. 컨테이너와 쿠버네티스 등의 컨테이너 오케스트레이션을 사용해 인프라를 구축, 운영하므로 특정 클라우드 서비스에 종속되지 않고 공통 인프라를 구축할 수 있게 함
2. `마이크로서비스로 애플리케이션 현대화`
   1. 마이크로서비스와 테스트 자동화를 근간으로 한 데브옵스를 실현
   2. 애플리케이션 개발, 변경만 신속하게 하는 것이 아니라 자동화를 통해 오류를 줄여 애플리케이션 품질을 향상시킨다.
3. `시스템 도입 방법 개선`
   1. 인습을 타파하고 신속하고 다이나믹하게 IT 시스템을 개발/운영하기 위해서는 IT 시스템 개발 및 구축을 내재화 해야 함

<br>

### DX 추진을 위한 방침

- 비즈니스 프로세스를 효율적으로 운영하기 위해서는 IT를 최대한 활용해야 한다. 가능한 `자동화`를 도모하고 조직이 프로세스를 `신속하게` 돌릴 수 있도록 노력해야 한다.

<br>

## 제2장. 클라우드 네이티브 컴퓨팅과 마이크로서비스

### 클라우드 컴퓨팅의 발자취

1. `REST`
   1. 타인이 제공하는 서비스를 인터넷을 통해 호출하면서 클라이언트 요청을 처리한다.의 역할을 크게 한 것이 RESTful 웹 서비스
   2. 기술적으로 침체기에 있던 웹서비스의 존재 가치를 바꾼 것이 웹 2.0 분을 통해 주목을 받은 REST다.
   3. HTTP는 원래 웹 서비스 구현에 필요한 구조를 갖춘 프로토콜임을 명확히 한 것이다.
   4. 이후 SaaS 애플리케이션의 API로 사용된다.
2. `클라우드 서비스 모델`
   1. 애플리케이션 개발/운영의 혁신으로 지속적 통합(CI)와 지속적 전달(CD), 데브옵스, 애자일 등 개발 프로세스가 주목을 받기 시작했고 클라우드 컴퓨팅을 형성하는 기법으로 자리잡았다.
   2. 이 기술들이 관심을 받은 계기는 애플리케이션 개발/운영의 속도 향상과 유연성을 실현하기 위해서였다.
   3. 지금까지 해온 것과 같은 속도로 애플리케이션을 개발한다면 클라우드 사용이 의미가 없다.
   4. 마이크로서비스란, 인프라 구축의 빠른 속도에 맞추어 애플리케이션 개발과 운영을 적시에 진행하기 위한 설계, 개발, 운영 기법을 모은 것이다. 여기서 핵심이 되는 것은 서비스라고 하는 독립적으로 개발 및 실행되는 소프트웨어 컴포넌트를 여러 개 조합해서 하나의 애플리케이션으로 만드는 소프트웨어 구조에 있다.
      이런 클라우드를 전제로 설계, 구축, 개발, 운영하는 컴퓨팅 스타일을 클라우드 네이티브 컴퓨팅이라고 한다.

<br>

### 클라우드 네이티브 컴퓨팅

- 클라우드 네이티브 컴퓨팅의 목적은 확장 가능한 애플리케이션을 구축/운영하는 것과 IT 시스템에 최소한의 인력으로 자주, 그리고 계획한 만큼 임팩트가 있는 변경을 추가하는 것이다.
- 그 앞에 있는 비즈니스 쪽 목표는 불특정 다수의 비즈니스 트랜잭션에 대응할 수 있는 대규모 시스템을 신속하게 구축해서 시장이 필요로 하는 것을 유연하게 제공하는 것이다.
- DX가 요구하는 속도와 유연성을 실현하는 것이 클라우드 네이티브 컴퓨팅의 목표라고도 할 수 있다.
- 또한 오픈소스를 적극 적용하므로 서비스에 종속되지 않는 생태계 실현을 권장하고 있다.
  [Cloud Native Interactive Landscape](https://landscape.cncf.io/)

<br>

### 클라우드 네이티브 컴퓨팅을 지탱하는 기술 요소

- `컨테이너화`, `오케스트레이션`과 `어플리케이션의 정의`, `마이크로서비스`, `데브옵스`가 중요하다.
- 데브옵스는 클라우드 네이티브 컴퓨팅뿐만 아니라 기존 시스템이나 애플리케이션 개발에도 유용하다.
  [Cloud Native Trail Map](https://github.com/cncf/trailmap)

<br>

1. `컨테이너`
   1. 컨테이너의 특징은 리눅스 커널 기능을 이용해서 OS 수준의 가상 환경을 실현했다는 것이다.
   2. 컨테이너형에서는 각 가상 환경 이미지가 OS를 지니지 않아도 되므로 가상 환경 배포나 실행이 빠르다는 장점이 있다.
   3. 컨테이너형 가상화에서는 컨테이너화 된 애플리케이션을 다른 곳에 이식하기도 쉬워서 비용 투자 관점에서도 장점이 있다.
2. `컨테이너 오케스트레이션`
   1. 컨테이너를 채택한 경우에는 클러스터 구성과 관리가 더 중요해진다고 볼 수 있다.
   2. 기존 아키텍처에 비해 클라우드 네이티브에서 관리해야 할 클러스터 멤버 수가 훨씬 더 늘어나는 것이다. 이 컨테이너들을 일일히 명령어를 입력해서 구성, 관리하는 것은 현실적이지 않으며, 이때 필요한 것이 바로 컨테이너 오케스트레이션이다.
   3. 클라우드 기반을 지탱하는 운영체제처럼 인프라 운영 기능을 제공하고, 컨테이너 애플리케이션의 생명 주기를 관리하는 것이 컨테이너 오케스트레이션의 역할이다.
3. `데브옵스`
   1. 데브옵스란 개발팀과 운영팀의 연계를 통해 신속하고 빈번하게, 그리고 확실하게 개발 및 테스트와 릴리스를 목표로 하는 것이다.
   2. CD란 짧은 주기로 소프트웨어를 릴리스하기 위한 소프트웨어 엔지니어링 기법으로서 이를 실현하게 해주는 거싱 바로 배포 파이프라인(CD 파이프라인)이다.
   3. 배포 파이프라인이란 컴파일, 빌드, 테스트, 배포를 자동화해 주는 툴 및 솔루션이다.
   4. 데브옵스를 통한 문화 혁신 중에서 '기법'을 대상으로 적용해야 하는 것이 애자일 개발 프로세스이며, '효율화'를 위해 활용해야 하는 것이 CD의 배포 파이프라인이다. 그리고 데브옵스는 '조직 혁신'을 포함한 전체를 통합해서 일관성을 유지하게 해주는 프레임워크라고 보면 된다.

<br>

### 클라우드 네이티브 컴퓨팅을 진행하는 이유

1. IT 시스템 `개발/운영 속도` 향상 및 `품질` 향상
2. `확장성`, `고가용성` (하이브리드 클라우드환경도 구축 가능)
3. `비용 절감` - 컨테이너 애플리케이션을 한 번 만들어 두면, 다른 플랫폼으로 쉽게 마이그레이션이 가능

<br>

### 마이크로서비스란?

마이크로서비스란, 클라우드 네이티브 컴퓨팅의 핵심이 되는 기술로 클라우드 기반에 특화된 애플리케이션, 즉 '클라우드 네이티브 애플리케이션' `개발/운영 아키텍처 스타일`이다.

<br>

### 마이크로서비스 아키텍처

- 핵심은 독립적으로 개발 및 실행되는 소프트웨어 컴포넌트를 여러 개 조합해서 하나의 애플리케이션을 구축하는 소프트웨어 구조에 있다. 이것을 구체화하기 위한 기술로 컨테이너, 오케스트레이션, REST, 메시징 등이 있으며, 기법으로는 데브옵스, 애자일 개발 프로세스, CD, 도메인 주도 설계가 있다.

- 마이크로서비스 아키텍처를 사용해 애플리케이션을 독립된 소프트웨어 컴포넌트, 즉 서비스로 분할하는 것이다. 그리고 하나의 요청을 처리하기 위해 각 서비스는 REST나 메시징으로 통신하는 분산 컴퓨팅 환경을 구성한다.

* 마이크로서비스 적용의 장점은 세밀한 소프트웨어 구조이다. 일부를 단계적으로 릴리스 및 변경하게 하는 유연성을 가져다준다. 스케일아웃이나 스케일인 관점에서 요청이 집중돼 있는 서비스만 확장 또는 축소할 수 있어서 시스템 리소스의 최적 사용 및 가동률 개선에 기여한다.

* 나쁜 영향을 초래하기도 한다. 사용자 요청이 발생할 때마다 서비스간 통신이 발생 -> 성능 영향을 미친다.
* 애플리케이션 뿐만 아니라 데이터도 분산 배치 되므로 DB간 일관성이나 동기화 기법, 운영 및 감시 구조를 정비해야 한다.
* 시스템 전체 설계의 일관성도 고려해야 한다.

<br>

**그럼에도 불구하고, 유연한 모듈 구조로 애플리케이션의 개별 유지/보수를 실현하고, DX를 실천하기 위해 가장 중요한 속도와 유연성이 있다.**

<br>

### 마이크로서비스의 특징

1. `서비스를 사용한 컴포넌트 설계`
   1. 모놀리식보다 간단하고 가벼운 통신기법(REST, 경량메시지)을 사용한다.
2. `개발/운영 체제`
   1. 마이크로서비스의 목표는 3계층 구조의 웹 애플리케이션을 만드는 것이 아니라, 독립된 운영이 가능한 서비스를 만드는 것이다.
3. `개발 환경과 영구 데이터 저장소의 거버넌스`
   1. 마이크로서비스에서는 프로그래밍 언어나 데이터베이스를 각 개발/운영팀이 선정하게 한다.
   2. 적합한 사유에 따라 다른 프로그래밍 언어나 데이터베이스를 사용할 수도 있다.
4. `인프라 환경 고려 사항`
   1. 마이크로서비스에서는 인프라 환경 구축, 소프트웨어 컴파일, 빌드, 테스트, 배포 자동화 등의 CD를 권장한다.
   2. 장애 발생을 전제로 한 설계를 제안한다.
   3. 각 서비스가 로그 및 트레이스 기능을 고현하는 것은 물론이고, 서버 및 네트워크의 메트릭을 감시해서 적시에 장애를 감지하고 대응할 것을 추천하고 있다.

<br>

### 마이크로서비스의 적용 기준

- 마이크로서비스를 적용하려면 기존과 다른 조직 체제와 애자일 개발 프로세스 실천, 도메인 분석과 서비스 모델링, 인프라 구축의 자동화, 분산 시스템 환경 운영 및 감시, 분산 배치된 데이터베이스의 동기화 등 큰 도전 과제가 기다리고 있다.
- 마이크로서비스는 `대규모`이면서 `복잡한 시스템`에 적당하다.
