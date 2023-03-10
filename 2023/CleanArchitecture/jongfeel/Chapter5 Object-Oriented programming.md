## 5장 객체 지향 프로그래밍

좋은 아키텍처를 만드는 일은 객체 지향Object-Oriented oo 설계 원칙을 이해하고 응용하는 데서 출발한다.

### 캡슐화?

C 언어: 헤더와 구현부를 분리해서 OO 구현
C++ 언어: 헤더에 멤버 변수가 존재한다는 사실을 알게 된다. 물론 private을 통해 멤버 변수를 접근하는 걸 컴파일러가 막긴 한다.
Java, C#: 헤더와 구현체를 모두 버려서 캡슐화는 더욱 심하게 훼손되었다.

OO가 강력한 캡슐화에 의존한다는 정의는 받아들이기 힘들다.
실제로 많은 OO 언어가 캡슐화를 거의 강제하지 않는다. Python, JavaScript, Ruby 등

OO 프로그래밍은 프로그래머가 충분히 올바르게 행동함으로써 캡슐화된 데이터를 우회해서 사용하지 않을 거라는 믿음을 기반으로 한다.

### 상속?

OO 언어가 고안되기 훨씬 이전에도 상속과 비슷한 기법이 사용되었다고 말할 수 있다.
하지만 상속을 흉내내는 요령은 있었지만, 상속만큼 편리한 방식은 절대 아니다.

OO 언어가 완전히 새로운 개념을 만들지는 못했지만, 데이터 구조에 가면을 씌우는 일을 상당히 편리한 방식으로 제공했다고 볼 수는 있다.

### 다형성?

함수를 가리키는 포인터를 응용한 것이 다형성이다.
따라서 OO가 새롭게 만든 것은 전혀 없다.
OO 언어는 다형성을 제공하지는 못했지만, 다형성을 좀 더 안전하고 더욱 편리하게 사용할 수 있게 해준다.

다형성을 구현하는 건, 함수 포인터를 직접 사용하여 만드는 방식이므로 위험하고, 특정 관례를 수동으로 따르는 방식이다.
OO 언어는 이러한 관례를 없애주며, 실수할 위험이 없다. 따라서 다형성을 구현하는게 대수롭지 않은 일이 된다.
OO는 제어흐름을 간접적으로 전환하는 규칙을 부과한다고 결론지을 수 있다.

#### 다형성이 가진 힘

입출력 드라이버에 대해 다형성을 구현한다면, 복사 프로그램인 이 드라이버를 얼마든지 사용할 수 있게 된다.

플러그인 아키텍처plugin architecture는 입출력 장치 독립성을 지원하기 위해 만들어졌고, 등장 이후 거의 모든 운영체제에서 구현되었다.

#### 의존성 역전

소스 코드 의존성의 방향은 반드시 제어흐름flow of control을 따르게 된다.
모든 호출 함수는 피호출 함수가 포함된 모듈의 이름을 명시적으로 지정해야 한다.
즉, 제어흐름은 시스템의 행위에 따라 결정되며, 소스 코드 의존성은 제어흐름에 따라 결정된다.

소스 코드와 제어 흐름이 반대로 된다면, 의존성 역전dependency inversion 현상이 일어나며
소프트웨어 아키텍트 관점에서 이러한 현상은 심오한 의미를 갖는다.
소프트웨어 아키텍트는 시스템의 소스 코드 의존성 전부에 대해 방향을 결정할 수 있는 절대적인 권한을 갖는다.

이것이 힘이다!
이것이 바로 OO가 제공하는 힘이다.
그리고 이것이 바로 OO가 지향하는 것이다.

컴포넌트 또는 배포 가능한 단위로 별도의 단위 로직을 컴파일 하고 독립적으로 배포해서 사용할 수 있다.
이것이 배포 독립성independent deployability이다.
모듈을 독립적으로 배포할 수 있게 되면, 서로 다른 팀에서 각 모듈을 독립적으로 개발할 수 있다.
이것이 개발 독립성independent developability이다. 

### 결론

OO란 다형성을 이용하여 전체 시스템의 모든 소스 코드 의존성에 대한 절대적인 제어 권한을 획득할 수 있는 능력이다.
OO를 사용하면 아키텍트는 플러그인 아키텍처를 구성할 수 있고,
이를 통해 고수준의 정책을 포함하는 모듈은 저수준의 세부사항을 포함하는 모듈에 대해 독립성을 보장할 수 있다.