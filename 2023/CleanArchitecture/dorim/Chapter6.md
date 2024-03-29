## 6장 함수형 프로그래밍

### 요약

- 가변 변수는 프로그램 실행 중에 상태가 변할 수 있다.
- 함수형 언어에서 변수는 변경되지 않는다.
- 아키텍트라면 **동시성** 문제에 지대한 관심을 가져야만 한다.
- 불변성과 관련하여 가장 주요한 타협 중 하나는 애플리케이션, 또는 애플리케이션 내부의 서비스를 가변 컴포넌트와 불변 컴포넌트로 분리하는 일이다. 불변 컴포넌트에서는 순수하게 함수형 방식으로만 작업이 처리되며, 어떤 가변 변수도 사용되지 않는다.
- 애플리케이션을 제대로 구조화하려면 변수를 변경하는 컴포넌트와 변경하지 않는 컴포넌트를 분리해야 한다는 것이다. 그리고 이렇게 분리하면 가변 변수들을 보호하는 적절한 수단을 동원해 뒷받침해야한다.
- 현명한 아키텍트라면 가능한 한 많은 처리를 불변 컴포넌트로 옮겨야 하고, 가변 컴포넌트에서는 가능한 한 많은 코들르 빼내야 한다.
- 이벤트 소싱은 상태가 아닌 트랜잭션을 저장하자는 전략이다. 상태가 필요해지면 단순히 상태의 시작점부터 모든 트랜잭션을 처리한다.
- 구조적 프로그래밍은 제어흐름의 **직접적인 전환**에 부과되는 규율이다.
- 객체 지향 프로그래밍은 제어흐름의 **간접적인 전환**에 부과되는 규율이다.
- 함수형 프로그래밍은 **변수 할당**에 부과되는 규율이다.
- 소프트웨어, 즉 컴퓨터 프로그램은 **순차**, **분기**, **반복**, **참조**로 구성된다. 그 이상도 이하도 아니다.
