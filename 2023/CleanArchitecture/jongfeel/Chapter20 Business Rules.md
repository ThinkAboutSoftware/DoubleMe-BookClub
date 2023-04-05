## 20장 업무 규칙

엄밀하게 말하면 업무 규칙은 사업적으로 수익을 얻거나 비용을 줄일 수있는 규칙 또는 절차다. 더 엄밀하게 말하면 컴퓨터상으로 구현했는지와 상관없이, 업무 규칙은 사업적으로 수익을 얻거나 비용을 줄일 수 있어야 한다.

핵심 업무 규칙은 보통 데이터를 요구한다. 핵심 규칙과 핵심 데이터는 본질적으로 결합되어 있기 때문에 객체로 만들 좋은 후보가 된다. 우리는 이러한 유형의 객체를 엔티티Entity라 부른다.

### 엔티티

엔티티는 컴퓨터 시스템 내부의 객체로서, 핵심 업무 데이터를 기반으로 동작하는 일련의 조그만 핵심 업무 규칙을 구체화한다. 엔티티 객체는 핵심 업무 데이터를 직접 포함하거나 핵심 업무 데이터에 매우 쉽게 접근할 수 있다. 엔티티의 인터페이스는 핵심 업무 데이터를 기반으로 동작하는 핵심 업무 규칙을 구현한 함수들로 구성된다.

엔티티는 순전히 업무에 대한 것이며, 이외의 것은 없다. 유일한 요구조건은 핵심 업무 데이터와 핵심 업무 규칙을 하나로 묶어서 별도의 소프트웨어 모듈로 만들어야 한다는 것이다.

### 유스케이스

자동화된 시스템이 동작 하는 방법을 정의하고 제약함으로써 수익을 얻거나 비용을 줄이는 업무 규칙도 존재한다. 이러한 규칙은 자동화된 시스템의 요소로 존재해야만 의미가 있으므로 수동 환경에서는 사용될 수 없다.

유스케이스는 자동화된 시스템이 사용 되는 방법을 설명한다. 유스케이스는 사용자가 제공해야 하는 입력, 사용자 에게 보여줄 출력, 그리고 해당 출력을 생성하기 위한 처리 단계를 기술한다.
엔티티 내의 핵심 업무 규칙과는 반대로, 유스케이스는 애플리케이션에 특화된 application-specific 업무 규칙을 설명한다.

유스케이스는 시스템이 사용자에게 어떻게 보이 는지를 설명하지 않는다. 이보다는 애플리케이션에 특화된 규칙을 설명하 며, 이를 통해 사용자와 엔티티 사이의 상호작용을 규정한다. 시스템에서 데이터가 들어오고 나가는 방식은 유스케이스와는 무관하다.

엔티티는 수많은 다양한 애플리케 이션에서 사용될 수 있도록 일반화된 것이므로, 각 시스템의 입력이나 출력 에서 더 멀리 떨어져 있다. 유스케이스는 엔티티에 의존한다. 반면 엔티티는 유스케이스에 의존하지 않는다.

### 요청 및 응답 모델

유스케이스는 단순한 요청 데이터 구조를 입력으로 받아들이고, 단순한 응답 데이터 구조를 출력으로 반환한다. 이들 데이터 구조는 어떤 것에도 의존하지 않는다.

의존성을 제거하는 일은 매우 중요하다. 요청 및 응답 모델이 독립 적이지 않다면, 그 모델에 의존하는 유스케이스도 결국 해당 모델이 수반하는 의존성에 간접적으로 결합되어 버린다.

### 결론

업무 규칙은 사용자 인터페이스나 데이터베이스와 같은 저수준의 관심사로 인해 오염되어서는 안 되며, 원래 그대로의 모습으로 남아 있어야 한다.
이상적으로는 업무 규칙을 표현하는 코드는 반드시 시스템의 심장부에 위치 해야 하며, 덜 중요한 코드는 이 심장부에 플러그인되어야 한다. 업무 규칙은 시스템에서 가장 독립적이며 가장 많이 재사용할 수 있는 코드여야 한다.