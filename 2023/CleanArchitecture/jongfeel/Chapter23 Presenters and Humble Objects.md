## 23장 프레젠터와 험블 객체

프레젠터는 험블 객체humble object 패턴을 따른 형태로, 아키텍처 경계를 식별하고 보호하는 데 도움이 된다.

### 험블 객체 패턴

험블 객체 패턴은 디자인 패턴으로, 테스트하기 어려운 행위와 테스트하기 쉬운 행위를 단위 테스트 작성자가 분리하기 쉽게 하는 방법으로 고안되었다.

### 프레젠터와 뷰

뷰는 험블 객체이고 테스트하기 어렵다. 프레젠터는 테스트하기 쉬운 객체다.
뷰는 뷰 모델의 데이터를 화면으로 로드할 뿐이며, 이 외에 뷰가 맡은 역할은 전혀 없다. 따라서 뷰는 보잘것없다humble

### 테스트와 아키텍처

행위를 테스트하기 쉬운 부분과 테스트하기 어려운 부분으로 분리하면 아키텍처 경계가 정의된다.
프레젠터와 뷰 사이의 경계는 이러한 경계 중 하나이다.

### 데이터베이스 게이트웨이

데이터베이스 게이트웨이는 다형적 인터페이스로, 애플리케이션이 데이터베이스에 수행하는 생성, 조회, 갱신, 삭제 작업과 관련된 모든 메서드를 포함한다.

### 데이터 매퍼

객체 관계 매퍼Object Relational Mapper, ORM 같은 건 사실 존재하지 않는다. 객체는 데이터 구조가 아니기 때문이다. 최소한 객체를 사용하는 사람 관점에서 객체는 데이터 구조가 아니다.

객체와 달리 데이터구조는 함축된 행위를 가지지 않는 public 데이터 변수의 집합이다. ORM 보다는 데이터 매퍼Data Mappter라고 부르는 것이 나은데, 관계형 데이터베이스 테이블로부터 가져온 데이터를 데이터 구조에 맞게 담아주기 때문이다.

ORM은 어디에 위치해야 하는가? 데이터베이스 계층이다. ORM은 게이트웨이 인터페이스와 데이터베이스 사이에서 일종의 또 다른 험블 객체 경계를 형성한다.

### 서비스 리스너

애플리케이션이 다른 서비스와 통신해야 한다면, 여기에서 서비스 경계를 생성하는 험블 객체 패턴을 발견할 수 있다.

### 결론

경계를 넘나드는 통신은 간단한 데이터 구조를 수반할 때가 많고, 그 경계는 테스트하기 어려운 것과 쉬운 것으로 분리될 것이다.
이러한 아키텍처 경계에서 험블 객체 패턴을 사용하면 전체 시스템의 테스트 용이성을 크게 높일 수 있다.