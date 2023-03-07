## Part 3 설계 원칙

좋은 벽돌로 좋은 아키텍처를 정의하는 원칙이 필요한데, 그게 SOLID이다.

SOLID 원칙의 목적은 중간 수준의 소프트웨어 구조가 아래와 같도록 만드는 데 있다.

- 변경에 유연하다.
- 이해하기 쉽다.
- 많은 소프트웨어 시스템에 사용될 수 있는 컴포넌트의 기반이 된다.

'중간 수준'이라 함은 프로그래머가 이들 원칙을 모듈 수준에서 작업할 때 적용할 수 있다는 뜻이다.
즉, 코드 수준보다는 조금 상위에서 적용되며 모듈과 컴포넌트 내부에서 사용되는 소프트웨어 구조를 정의하는 데 도움을 준다.

## 7장 SRP: 단일 책임 원칙

단 하나의 일만 해야 한다는 원칙은 함수는 반드시 하나의, 단 하나의 일만 해야 한다는 원칙이다.
이 원칙은 커다란 함수를 작은 함수들로 리팩터링하는 더 저수준에서 사용된다.

SRP는 아래와 같이 기술되어 왔다.

> 단일 모듈은 변경의 이유가 하나, 오직 하나뿐이어야 한다.

소프트웨어 시스템은 사용자와 이해관계자를 만족시키기 위해 변경된다.
SRP가 말하는 '변경의 이유'란 사용자와 이해관계자를 가리킨다.
이 원칙은 아래와 같이 바꿔 말할 수도 있다.

> 하나의 모듈은 하나의, 오직 하나의 사용자 또는 이해관계자에 대해서만 책임져야 한다.

시스템이 동일한 방식으로 변경되기를 원하는 사용자나 이해관계자가 두 명 이상일 수도 있다.
이러한 집단을 액터actor라고 할 때 SRP의 최종 버전은 아래와 같다.

> 하나의 모듈은 하나의, 오직 하나의 액터에 대해서만 책임져야 한다.

'모듈'은 소스 파일이라고 볼 수 있다.
일부 언어와 개발 환경에서는 코드를 소스 파일에 저장하지 않기 때문에 
모듈은 함수와 데이터 구조로 구성된 응집된 집합으로 볼 수 있다.

'응집된cohesive'이라는 단어가 SRP를 암시한다.
단일 액터를 책임지는 코드를 함께 묶어주는 힘이 바로 응집성cohesion이다.

### 징후 1: 우발적 중복

Employee 클래스에 세 가지 메서드 calculatePay(), reportHours(), save()가 있다면
이 클래스는 세 가지 메서드가 서로 다른 세 명의 액터를 책임지기 때문에 SRP 위반이다.

- calculatePay() 메서드는 회계팀에서 기능을 정의하며, CFO 보고를 위해 사용한다.
- reportHours() 메서드는 인사팀에서 기능을 정의하고 사용하며, COO 보고를 위해 사용한다.
- save() 메서드는 데이터베이스 관리자DBA가 기능을 정의하고, CTO 보고를 위해 사용한다.

예를 들어 calculatePay() 메서드와 reportHours() 메서드가 초과 근무를 제외한 업무시간을 알고리즘을 공유한다고 했을 때,
이 알고리즘을 regualrHours()라는 메서드에 넣었다고 하면
개발자는 calculatePay() 메서드가 편의 메서드인 regularHours()를 호출한다는 사실을 발견한다.
하지만 이 함수가 reportHours() 메서드에서도 호출된다는 사실은 눈치채지 못한다.

이런 문제는 서로 다른 액터가 의존하는 코드를 너무 가까이 배치했기 때문에 발생한다.
SRP는 서로 다른 액터가 의존하는 코드를 서로 분리하라고 말한다.

### 징후 2: 병합

소스 파일에 다양하고 많은 메서드를 포함하면 병합이 자주 발생한다.
메서드가 서로 다른 액터를 책임진다면 병합이 발생할 가능성은 확실히 더 높다.

최근 병합 도구는 굉장히 뛰어나지만, 어떤 도구도 병합이 발생하는 모든 경우를 해결할 수는 없다.
결국 병합에는 항상 위험이 뒤따르게 된다.

이 문제를 벗어나려면 서로 다른 액터를 뒷받침하는 코드를 서로 분리하는 것이다.

### 해결책

메서드를 각기 다른 클래스로 이동시킨다.

1.
확실한 해결책으로 데이터와 메서드를 분리하는 방식이다.
아무런 메서드가 없는 간단한 데이터 구조인 EmployeeData 클래스를 만들어 ,세 개의 클래스가 공유하도록 한다.
세 클래스는 서로의 존재를 몰라야 한다, 따라서 '우연한 중복'을 피할 수 있다.

2.
이 방법은 세 클래스를 인스턴스화 하고 추적해야 하는게 단점이므로
파사드Facade 패턴을 사용할 수 있다.
EmployeeFacade는 코드가 거의 없고 이 클래스는 세 클래스의 객체를 생성하고 요청된 메서드를 가지는 객체로 위임하는 일을 책임진다.

3.
중요한 업무 규칙을 데이터와 가깝게 배치하는 방식을 선호하는 경우라면
Employee 클래스에 중요 메서드는 유지하고 덜 중요한 나머지 메서드들에 대해 파사드를 사용할 수도 있다.

모든 클래스는 반드시 단 하나의 메서드를 가져야 한다는 주장에 근거하여 앞의 해결책에 반대할 수도 있지만 이는 현실과는 다르다.
각 클래스에서 필요한 메서드의 개수는 훨씬 더 많을 수 밖에 없으며 다수의 private 메서드를 포함할 것이다.

### 결론

단일 책임 원칙은 메서드와 클래스 수준의 원칙이다.
하지만 이보다 상위의 두 수준에서도 다른 형태로 다시 등장한다.
컴포넌트 수준에서는 공통 폐쇄 원칙Common Closure Principle이 된다.
아키텍처 수준에서는 아키텍처 경계Architectural Boundary의 생성을 책임지는 변경의 축Axis of Change이 된다.