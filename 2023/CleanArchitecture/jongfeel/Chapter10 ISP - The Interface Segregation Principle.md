## 10장 ISP: 인터페이스 분리 원칙

다수의 사용자가 OPS 클래스의 오퍼레이션을 사용한다.
User1은 op1을
User2는 op2를
User3는 op3만을 이용한다.

OPS 클래스가 정적 타입 언어로 작성된 클래스라고 했을때
한 user의 메서드는 다른 두 user의 메서드에 관여하게 된다.
즉 op2 소스 코드가 변경 되면 User1도 다시 컴파일한 후 새로 배포해야 한다.

오퍼레이션을 인터페이스 단위로 분리하면 해결할 수 있다.

### ISP와 언어

정적 타입 언어는 사용자가 타입 선언문을 사용하도록 강제한다.
그래서 소스 코드에 '포함된included' 선언문으로 소스 코드 의존성이 발생하고,
재컴파일 또는 재배포가 강제되는 상황이 초래된다.

동적 타입 언어는 소스 코드에 선언문이 없고, 런타임 추론이 발생한다.
소스 코드 의존성이 없으므로 재컴파일과 재배포가 필요없다.

이런 사실로 ISP를 아키텍처가 아니라, 언어와 관련된 문제라고 결론내릴 여지가 있다.

### ISP와 아키텍처

소스 코드 의존성이 있는 경우 불필요한 재컴파일과 재배포를 하게 되므로
필요 이상으로 많은 걸 포함하는 모듈에 의존하는 것은 해로운 일이다.

### 결론

불필요한 점을 실은 무언가에 의존하면 예상치도 못한 문제에 빠진다