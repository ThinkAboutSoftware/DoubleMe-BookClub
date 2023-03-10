## 2장 두 가지 가치에 대한 이야기

행위behaviour
구조structure

### 행위

많은 프로그래머가 요구사항을 구현하고 버그를 수정하는 일이 자신의 직업이라고 믿는다.
슬픈 일이지만 그들은 틀렸다.

### 아키텍처

소프트웨어는 '부드러움을 지니도록' 만들어졌다.
소프트웨어를 만든 이유는 기계의 행위를 쉽게 변경할 수 있도록 하기 위해서다.

소프트웨어가 가진 본연의 목적을 추구하려면
변경하기 쉬워야 한다.
즉, 기능에 대한 변경이 일어나면 이런 변경 사항을 간단하고 쉽게 적용할 수 있어야 한다.

아키텍처가 특정 형태를 다른 형태보다 선호하면 할수록,
새로운 기능을 이 구조에 맞추는 게 더 힘들어진다.
아키텍처는 형태에 독립적이어야 하고, 그럴수록 더 실용적이다.

### 더 높은 가치

변경이 완전히 불가능한 프로그램이란 존재하지 않는다.
하지만 수정이 현실적으로 불가능한 시스템은 있는데,
변경에 드는 비용이 변경으로 창출되는 수익을 초과하는 경우다.

"변경 비용이 너무 커서 현실적으로 적용할 수 없다"라면
"실질적으로 변경이 불가능한 상태에 처할 때 까지 시스템을 방치했다"고 생각할 수 있다.

### 아이젠하워 매트릭스

![image](https://user-images.githubusercontent.com/17442457/219006584-16c1ed2a-dc44-4e85-bd6d-7b16615fe9b3.png)

> 긴급한 문제는 중요하지 않으며, 중요한 문제는 절대 긴급하지 않다.

소프트웨어의 가치에서
첫 번째, 행위는 긴급하지만 매번 높은 중요도를 가지는 것은 아니다.
두 번째, 아키텍처는 중요하지만 즉각적인 긴급성을 필요로 하는 경우는 절대 없다.

업무 관리자는 보통 아키텍처의 중요성을 평가할 만한 능력을 겸비하지 못하기 때문에 개발자는 딜레마에 빠진다.
기능의 긴급성이 아닌 아키텍처의 중요성을 설득하는 일은 소프트웨어 개발팀이 마땅히 책임져야 한다. 

### 아키텍처를 위해 투쟁하라

이러한 책임을 다하려면 투쟁해야 한다. 
효율적인 소프트웨어 개발팀은
이러한 투쟁에서 정면으로 맞서 싸우고
뻔뻔함을 무릅쓰고 다른 이해관계자들과 동등하게 논쟁한다.

소프트웨어 개발자는 소프트웨어를 안전하게 보호해야할 책임이 있으므로
이해관계자의 관계가 있다는 걸 알아야 한다.
이것이 역할이고 책무 중 하나다.

만약 소프트웨어 아키텍트라면 두 배로 중요해진다.
시스템이 제공하는 특성이나 기능 보다는 시스템의 구조에 더 중점을 둔다.
아키텍트는 이러한 특성과 기능을 개발하기 쉽고, 간편하게 수정할 수 있으며, 확장하기 쉬운 아키텍처를 만들어야 한다.

아키텍처가 후순위가 되면 시스템을 개발하는 비용이 더 많이 들고, 일부 또는 전체 시스템에 변경을 가하는 일이 현실적으로 불가능해진다.
이러한 상황이 발생하도록 용납했다면, 이는 결국 소프트웨어 개발팀이 스스로 옳다고 믿는 가치를 위해 충분히 투쟁하지 않았다는 뜻이다. 