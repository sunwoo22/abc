# Spring-study
스프링 개념 정리
<br><br>

## Contents
- [객체지향](#객체지향)
- [디자인 패턴](#디자인-패턴)
- [Web](#Web)
- [Spring](#Spring)
- [Spring Boot](#Spring-Boot)
- [Spring Boot 기능 활용](#Spring-Boot-기능-활용)
<br><br>

## 객체지향

<details>
<summary><b>객체지향의 등장</b></summary>

이전에는 C언어처럼 실행하고자 하는 순서대로 명령어를 입력해서 실행되는 **절차 지향**이 주를 이뤘으며, 이러한 방법으로 코딩하는 언어를 **절차지향 언어**라고 한다. 이 때에는 프로그램의 단위가 크지 않았으며, 대체적으로 간단한 Logic을 순차적으로 처리하여 결과를 얻는데 그쳤지만, 점점 컴퓨터의 발전과 이로 인하여 프로그램의 복잡도가 증가하면서 이에 들어가는 유지보수, 개발기간 등 다양한 부분에서 비효율이 발생했다.   
이런 어려움을 해결하기 위해 **효과적인 개발방식**을 채택하게 되었고, 이는 이전에 사용하던 흐름에 따른 개발 방식에서 벗어나 객체지향의 특성인 추상화, 상속, 은닉, 재사용, 인터페이스 등 여러 곳에서 객체지향으로 개발을 시작했다. 함수의 활용으로도 충분히 좋은 프로그램을 개발할 수 있었으나 새로운 시각으로 바라보기 시작했다.   
객체지향이란 현실에 존재하는 사물을 있는 그대로 모델링하여, 이들의 **행위와 속성을 정의**하고, 절차적이 아닌 객체가 중심이 되어 **실제 사물이 동작하는 방식으로 설계**하는 것이다. 이는 사물에 대해 **객체(Object)**라고 부르며, 해당 사물이 하는 **행위를 Method**로 정의하고 해당 사물이 가지는 속성을 **변수(Variable)**라고 정의한다. 실제 사물을 중심으로 설계하기 때문에 기존의 절차지향보다는 조금 더 **편리한 설계**가 가능해졌다.   
Java는 1995년 Sun Microsystems에서 작은 언어를 지향하는 객체지향 언어로 소개되었다. 당시 C++과 유사한 언어의 구문을 채택하였으나, C++이 가지고 있는 시스템 레벨 접근, 메모리 직접 할당 및 해제, 포인터 등 복잡한 개발 방식을 사용하지 않았다. 또한 어떠한 운영체제에서도 자바 가상 머신만 있으면 독립적으로 실행될 수 있도록 설계가 되어 있어, 여러 플랫폼에서 호환성을 제공하는 장점을 가진다.   
</details>
<br>

### 객체의 3가지 요소
<details>
<summary><b>객체의 상태</b> (상태 유지)</b></summary>

객체는 상태 정보를 저장하고, 유지되어져야 하며 이러한 속성(Variable)은 변수로 정의되어져야 한다.    
이러한 속성값이 바뀜으로 인하여, 객체의 상태가 변경될 수 있어야 한다.
</details>
<details>
<summary><b>객체의 책임</b> (기능 제공)</summary>

객체는 기능을 제공해야 한다. 이 부분은 Method의 제공으로 이루어진다.   
이 부분은 캡슐화와 연관이 있으며, 외부로부터 직접 속성에 접근하여 변경하는 것이 아닌 객체가 제공하는 Method로 기능이 제공되어져야 한다.
</details>
<details>
<summary><b>객체의 유일성</b> (고유 식별자 제공)</summary>

각각의 객체는 고유한 식별자를 가져야 한다.   
예를 들면 카드번호, 계좌번호, 자동차번호와 같은 속성을 통해서 각각 고유한 값을 줄 수 있으며,   
이는 이후 DB에서 Unique Key, 또는 Primary key로도 작성이 가능하다.
</details>
<br>

### 물리 객체와 개념 객체
<details>
<summary><b>물리 객체</b></summary>

물리적 객체는 실제로 사물이 존재하며, 이를 클래스로 정의한 객체를 의미한다.   
ex) 자동차 렌탈 시스템 : 자동차, 고객, 직원, 사업장, 정비소 등
</details>
<details>
<summary><b>개념 객체</b></summary>

웹 시스템에서 Service에 해당되며, 이는 Busineww logic을 처리하는 부분을 의미한다.   
Business logic에서는 여러 객체를 서로 상호작용하도록 하며,   
객체가 제공하는 오퍼레이션 Method를 통하여 객체의 속성을 변경한다.   
ex) 사용자 관리 시스템 : 사용자 객체의 마지막 접속일자를 이용하여 계정만료, 비밀번호 초기화, 재등록 처리 등
</details>
<br>

### 객체지향의 4대 특성
<details>
<summary><b>캡슐화</b></summary>
객체의 속성(Variable)을 보호하기 위해서 사용한다.
<br><br>
<p>

**Method 설계**
- 속성이 선언되었으나, 이의 상태를 변경하는 Method가 없다면, 잘못 선언된 속성이다. 즉, 자신이 가지고 있는 속성에 대해서는 해당 상태를 변경하는 기능을 제공해야 한다.
- 실물 객체가 가진 기능을 모두 제공해야 한다.
- 각각의 Method는 서로 관련성이 있어야 한다.
- 객체 안의 Method는 객체 안의 속성을 처리해야 하며, 다른 객체를 전달받아 해당 다른 객체에 정의된 속성을 직접 처리하면 안된다. 단, Method의 실행에 필요한 값들은 객체의 형태가 아닌 매개변수의 형태로 전달되어져야 한다.
- 외부에서 내부 속성(Variable)에 직접 접근하는 것이 아닌 Getter/Setter Method를 통해서 접근하도록 적용한다.
- 데이터 처리를 위한 기본적인 CRUD Method, Business logic 처리를 위한 Method, 객체의 생명 주기 처리 Method(disrtoy(), disconnect(), quit() 등), 객체의 영구성 관리 Method(영구성(유효성) 속성에 대한 변경이 필요한 경우, 외부에서는 접근이 불가능하도록 private로 선언하며, 내부의 다른 Method를 통해서 사용되도록 함)를 제공한다.
- Method의 속성은 반드시 1개에 속할 필요는 없으며, 여러 속성에 해당될 수 있다.
</p>
<p>

**장점**
- 객체지향의 패러다임 중 하나인 추상화를 제공한다. 실제로 Method가 어떻게 동작하는지 외부에서는 이해할 필요가 없으며, 이를 단순 호출만으로 해당 기능을 실행할 수 있고, 이를 통해서 객체 단위로 프로그램 설계가 가능하다.
- 재사용성과 유지보수의 효율성이 향상된다. 한 객체에 관련된 속성 및 Method는 모두 캡슐화의 형태로 제공되므로, 객체의 모듈성과 응집도가 높아진다. 만일 절차적 프로그래밍에서 Method를 재사용한다면, 함수가 참조하고 있는 전역변수 및 내부에서 호출하는 Method가 미치는 영향을 모두 체크해야 하나, 객체의 경우는 단일 객체에만 영향을 주기에 재사용성이 높다.
</p>
<p>

**무결성**
- 보통의 캡슐화 코딩이라고 하면 주로 변수는 private로 Method를 public으로 선언하는 형태를 많이 가지게 되는데, 이는 객체의 무결성을 위함이다.
- Getter/Setter를 제외하고는 public method는 입력된 매개변수를 Validation 한 후에 실행하는 것을 기본으로 한다.
- Validation을 통하여, 객체의 값을 바꾸거나 값에 대한 유효성을 가질 수 있다.
</p>
</details>
<details>
<summary><b>상속</b></summary>
객체지향에서의 상속은, 속성의 상속이 아닌 하위로 내려갈수록 구체화되는 것이다.
<br><br>

<p>

**상속의 효과**
- 프로그램 구조에 대한 이해도가 향상된다. 최상위 클래스의 구조를 보고, 하위 클래스의 동작을 이해할 수 있다.
- 재사용성이 높아진다. 상속을 이용하여 해당 클래스에 필요한 속성과 메소드를 모두 정의하지 않고, 상속을 받아 사용할 수 있다.
- 확장성이 높아진다. 일관된 형태의 클래스 객체를 추가할 수 있어, 간단하게 프로그램 확장이 가능하다.
- 유지보수성이 향상된다. 각 객체마다 자신의 메소드를 정의하고 있다면 코드 수정에서 많은 작업이 필요하지만, 상속을 사용한 경우 일관된 형태로 작성이 가능하다.
</p>
</details>
<details>
<summary><b>다형성</b></summary>
다형성은 하나의 개체가 여러 개의 형태로 변화하는 것을 말하며 이를 객체지향에서도 유사하게 사용한다. 다형성은 오버라이딩을 통해 가능하다.
</details>
<details>
<summary><b>추상화</b></summary>
객체지향에서의 추상화는 모델링이다. 구체적으로 공통적인 부분 또는 특정 특성을 분리하여 재조합하는 부분이 추상화이다. 다형성, 상속 모두 추상화에 속한다.
</details>
<br>

### 객체지향 설계 5원칙 SOLID
<details>
<summary><b>결합도와 응집도</b></summary>

좋은 소프트웨어 설계를 위해서는 결합도(coupling)는 낮추고 응집도(cohesion)는 높여야 한다.   
- **결합도** : 모듈(클래스) 간의 상호 의존 정도를 나타내는 지표로써 결합도가 낮으면 모듈간의 상호 의존성이 줄어들어서 객체의 재사용 및 유지보수가 유리하다.   
- **응집도**: 하나의 모듈 내부에 존재하는 구성 요소들의 기능적 관련성으로 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져 재사용 및 유지보수가 용이하다.
</details>

#### SOLID
<details>
<summary><b>SRP</b>(Single Responsibility Principle): 단일 책임 원칙</summary>
어떠한 클래스를 변경해야 하는 이유는 한가지 뿐이어야 한다.
</details>
<details>
<summary><b>OCP</b>(Open Closed Principle): 개방 폐쇄 원칙</summary>

자신의 확장에는 열려있고, 주변의 변화에 대해서는 닫혀있어야 한다.   
상위 클래스 또는 인터페이스를 중간에 둠으로써 자신은 변화에 대해서 폐쇄적이지만,   
인터페이스는 외부의 변화에 대해서 확장을 개방해줄 수 있다.   
이러한 부분은 JDBC와 Mybatis, Hibernate 등 Java에서는 Stream(Input/Out)에서 찾아볼 수 있다.
</details>
<details>
<summary><b>LSP</b>(Liskov Substitution Priciple): 리스코프 치환 원칙</summary>
서브 타입은 언제나 자신 기반(상위) 타입으로 교체할 수 있어야 한다.
</details>
<details>
<summary><b>ISP</b>(Interface Segregation Principle): 인터페이스 분리 원칙</summary>
클라이언트는 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안된다.   
프로젝트 요구 사항과 설계에 따라서 SRP(단일책임원칙)/ISP(인터페이스분리원칙)를 선택한다.
</details>
<details>
<summary><b>DIP</b>(Dependency Inversion Principle): 의존 역전 원칙</summary>
자신보다 변하기 쉬운 것에 의존하지 말아야 한다.
</details>
<br>

### POJO Java
<details>
<summary><b>POJO(Plain Old Java Object)</b></summary>
순수한 자바 오브젝트를 뜻한다.
</details>
<details>
<summary><b>특징</b></summary>

- 특정 규약에 종속되지 않는다.  
특정 Library, Module에서 정의된 클래스를 상속받아서 구현하지 않아도 된다.   
POJO가 되기 위해서는 외부에 의존성을 두지 않고, 순수한 Java로 구성이 가능해야 한다.
- 특정 환경에 종속되지 않는다.  
만일 특정 비즈니스 로직을 처리하는 부분에 외부 종속적인 http request, session 등이 있다면 POJO를 위배한 것으로 간주한다.   
또한 많이 사용하고 있는 @Annotation 기반으로 설정하는 부분도 엄연히는 POJO라고 볼 수 없다.
</details>

#### POJO Framework
<details>
<summary><b>Spring / Hibernate</b></summary>

하나의 서비스를 개발하기 위해서는 시스템의 복잡함, 비즈니스 로직의 복잡함 등 다양한 어려움을 맞이하게 된다.   
두 프레임워크는 객체지향적인 설계를 하고 있으며, 또한 개발자가 서비스 로직에 집중하고 이를 POJO로 쉽게 개발할 수 있도록 지원하고 있다.
</details>
<br>
<br>

## 디자인 패턴

### 디자인 패턴
<details>
<summary><b>디자인 패턴이란?</b></summary>

자주 사용하는 설계 패턴을 정형화해서 이를 유형별로 가장 최적의 방법으로 개발을 할 수 있도록 정해둔 설계이다.   
알고리즘과 유사하지만 명확하게 정답이 있는 형태는 아니며 프로젝트의 상황에 맞추어 적용 가능하다.
</details>
<details>
<summary><b>GOF 디자인 패턴</b></summary>

소프트웨어를 설계할 때는 기존의 경험이 매우 중요하다. 그러나 모든 사람들이 다양한 경험을 가지고 있을 수는 없다.   
이러한 지식을 공유하기 위해서 나온 것이 GOF(Gand of Four)의 디자인 패턴이다.   
객체지향 개념에 따른 설계 중 재사용할 경우 유용한 설계를 디자인 패턴으로 정리해둔 것이다.   
GOF의 디자인 패턴은 총 23개이며, 이를 잘 이해하고 활용한다면 경험이 부족하더라도 좋은 소프트웨어 설계가 가능하다.
</details>
<details>
<summary><b>장점 및 단점</b></summary>
<p>

**장점**
- 개발자(설계자) 간의 원활한 소통
- 소프트웨어 구조 파악 용이
- 재사용을 통한 개발 시간 단축
- 설계 변경 요청에 대한 유연한 대처
</p>
<p>

**단점**
- 객체지향 설계/구현
- 초기 투자 비용 부담
<p>
</details>
<br>

### 디자인 패턴의 종류
<details>
<summary><b>생성 패턴</b></summary>

객체를 생성하는 것과 관련된 패턴으로, 객체의 생성과 변경이 전체 시스템에 미치는 영향을 최소화하고 코드의 유연성을 높여준다.
- Factory Method
- Singleton
- Prototype
- Builder
- Abstract Factory
- Chaining
</details>
<details>
<summary><b>구조 패턴</b></summary>

프로그램 내의 자료구조나 인터페이스 구조 등 프로그램 구조를 설계하는 데 활용될 수 있는 패턴이다. 클래스, 객체들의 구성을 통해서 더 큰 구조를 만들 수 있게 해준다. 큰 규모의 시스템에서는 많은 클래스들이 서로 의존성을 가지게 되는데, 이런 복잡한 구조를 개발하고 유지보수하기 쉽게 만들어 준다.
- Adaper
- Compositer
- Bridge
- Decorator
- Facade
- Flyweight
- Proxy
</details>
<details>
<summary><b>행위 패턴</b></summary>

반복적으로 사용되는 객체들의 상호작용을 패턴화한 것으로, 클래스나 객체들이 상호작용하는 방법과 책임을 분산하는 방법을 제공한다. 행위 패턴은 행위 관련 패턴을 사용하여 독립적으로 일을 처리하고자 할 때 사용한다.
- Template Method
- Interpreter
- Iterator
- Observer
- Strategy
- Visitor
- Chain of responsibility
- Command
- Mediator
- State
- Memento
</details>
<br>

### 주요 디자인 패턴
<details>
<summary><b>Singleton Pattern</b></summary>
싱글톤 패턴은 어떠한 클래스(객체)가 유일하게 1개만 존재할 때 사용한다. 서로 자원을 공유할 때 주고 사용하는데, 실물 세계에서는 프린터가 해당되며 실제 프로그래밍에서는 TCP Socket 통신에서 서버와 연결된 connect 객체에 주로 사용한다.
</details>
<details>
<summary><b>Adapter Pattern</b></summary>
어댑터는 실생활에서는 110v를 220v로 변경해주거나, 그 반대로 해주는 흔히 돼지코라고 불리는 변환기를 예로 들 수 있다. 호환성이 없는 기존 클래스의 인터페이스를 변환하여 재사용할 수 있도록 한다. SOLID 중에서 OCP(개방폐쇄원칙)를 다른다.
</details>
<details>
<summary><b>Proxy Pattern</b></summary>
프록시는 대리인이라는 뜻으로, 뭔가를 대신해서 처리하는 것이다. 프록시 클래스를 통해서 대신 전달하는 형태로 설계되며 실제 Client는 프록시로부터 결과를 받는다. Cache의 기능으로도 활용이 가능하다. SOLID 중에서 OCP(개방폐쇄원칙)와 DIP(의존역전원칙)를 따른다.
</details>
<details>
<summary><b>Decorator Pattern</b></summary>
데코레이터 패턴은 기존 뼈대(클래스)는 유지하되, 이후 필요한 형태로 꾸밀 때 사용한다. 확장이 필요한 경우 상속의 대안으로도 활용한다. SOLID 중에서 OCP(개방폐쇄원칙)와 DIP(의존역전원칙)를 따른다.
</details>
<details>
<summary><b>Observer Pattern</b></summary>
관찰자 패턴은 변화가 일어났을 때, 미리 등록된 다른 클래스에 통보해주는 패턴을 구현한 것이다. Event listener에서 해당 패턴을 많이 사용하고 있다.
</details>
<details>
<summary><b>Facade Pattern</b></summary>
퍼사드는 건물의 앞쪽 정면이라는 뜻을 가진다. 여러 개의 객체와 실제 사용하는 서브 객체 사이에 복잡한 의존관계가 있을 때, 중간에 퍼사드라는 객체를 두고, 여기서 제공하는 인터페이스만을 활용하여 기능을 사용하는 방식이다. 퍼사드는 자신이 가지고 있는 각 클래스의 기능을 명확히 알아야 한다.
</details>
<details>
<summary><b>Strategy Pattern</b></summary>
전략 패턴으로 불리며 객체지향의 꽃이다. 유사한 행위들을 캡슐화하여 객체의 행위를 바꾸고 싶은 경우, 직접 변경하는 것이 아닌 전략만 변경하여 유연하게 확장하는 SOLID 중에서 OCP(개방폐쇄원칙)와 DIP(의존역전원칙)를 따른다. 전략 메서드를 가진 전략 객체, 전략 객체를 사용하는 컨텍스트, 전략 객체를 생성해 컨텍스트에 주입하는 클라이언트로 구성되어 있다.
</details>
<br>
<br>

## Web

### Web
<details>
<summary><b>Web이란?</b></summary>
Web(World Wide Web, WWW, W3)은 인터넷에 연결된 컴퓨터를 통해 사람들이 정보를 공유할 수 있는 전 세계적인 정보 공간을 말한다.
</details>
<details>
<summary><b>Web의 용도</b></summary>

- **Web Site** :   
google, naver, daum, facebook 등 HTML로 구성된 여러 사이트들
- **API**(Application Programming Interface) * **Web Service** :   
Google Open API, Naver Open API, Kakao Open API 등
- **User Interface** :   
Chrome, Safari, Explorer, Smart Watch, IP TV 등
</details>
<details>
<summary><b>Web의 기반</b></summary>

- **HTTP**(Hypertext Transfer Protocol) : 
어플리케이션 컨트롤
- **URI**(Uniform Resouce Identifier) : 
리소스 식별자. 모든 정모에 접근할 수 있는 정보
- **HTML**(Hyper Text Markp Language) : 
하이퍼미디어 포맷. XML을 바탕으로 한 범용 문서 포맷
</details>
<br>

### REST
<details>
<summary><b>REST(Representational State Trasfer)</b></summary>
직역하면 자원의 상태 전달이며, 네트워크 아키텍쳐를 의미한다.
</details>
<details>
<summary><b>특징</b></summary>

- **Client/Server** : 클라이언트와 서버가 서로 독립적으로 분리되어 있어야 한다.
- **Stateless** : 요청에 대해서 클라이언트의 상태를 서버에 저장하지 않는다.
- **Cache** : 클라이언트는 서버의 응답을 Cache(임시저장) 할 수 있어야 한다.
- **계층화(Layered System)** : 서버와 클라이언트 사이에 방화벽, 게이트웨이, 프록시 등 다양한 계층 형태로 구성이 가능해야 하며, 이를 확장할 수 있어야 한다.
- **인터페이스 일관성** : 인터페이스의 일관성을 지키고 아키텍쳐를 단순화시켜 작은 단위로 분리하여 클라이언트, 서버가 독립적으로 개선될 수 있어야 한다.
- **Code on Demand(Optional)** : 자바 애플릿, 자바스크립트, 플래시 등 특정한 기능을 서버로부터 클라이언트가 전달받아 코드를 실행할 수 있어야 한다.
</details>
<details>
<summary><b>인터페이스 일관성</b></summary>

아래의 조건들을 잘 갖춘 경우 RESTful하다고 표현하고 이를 REST API라고 부른다.
- **자원의 식별** :   
웹 기반의 REST에서는 리소스 접근을 할 때 URI를 사용한다.
- **메시지를 통한 리소스 조작** :   
Web에서는 다양한 방식으로 데이터를 전달하는데 그 중에서 가장 많이 사용하는 방식은 HTML, XML, JSON, TEXT 등이 있다. 이 중에서 어떠한 타입의 데이터인지 알려주기 위해서 HTTP Header 부분에 content-type을 통해 데이터의 타입을 지정해줄 수 있다. 또한 리소스 조작을 위해 데이터 전체를 전달하지 않고 메세지 형태로 데이터를 주고받으로, client-server가 독립적으로 확장 가능하도록 한다.
- **자기 서술적 메세지** :   
요청하는 데이터가 어떻게 처리되어져야 하는지 충분한 데이터를 포함할 수 있어야 한다. HTTP 기반의 REST에서는 HTTP Method와 Header 정보, URI에 포함되는 정보로 표현할 수 있다. 그 외에 담지 못한 정보들은 URI의 메세지를 통하여 표현한다.
- **Application 상태에 대한 엔진으로써 하이퍼미디어** :   
REST API를 개발할 때 단순히 Client 요청에 대한 데이터만 응답해주는 것이 아닌 관련된 리소스에 대한 Link 정보까지 같이 포함되어야 한다.
</details>
<br>

### URI 설계 패턴
<details>
<summary><b>URI > URL</b></summary>
URL은 URI의 하위 개념이다.
</details>
<details>
<summary><b>URI(Uniform Resource Identifier)</b></summary>

인터넷에서 특정 자원을 나타내는 주소값으로 해당 값은 유일하다(응답은 달라질 수 있음).
- 요청: https://www.ex.co.kr/resource/sample/1
- 응답: example.pdf, example.doc
</details>
<details>
<summary><b>URL(Uniform Resource Locator)</b></summary>

인터넷 상에서의 자원, 특정 파일이 어디에 위치하는지 식별하는 주소이다.
- 요청: https://www.ex.co.kr/example.pdf
</details>
<details>
<summary><b>URI 설계 원칙 (RFC-3986)</b></summary>

- 슬래시 구분자(/)는 계층 관계를 나타내는 데 사용한다.<br>
https://ex.co.kr/classes/java/curriculums
- URI 마지막 문자로 /는 포함하지 않는다.<br>
https://ex.co.kr/classes/java/curriculums/ (X)
- 하이픈(-)은 URI 가독성을 높이는 데 사용한다.<br>
https://ex.co.kr/classes/java/curriculums/web-master
- 언더바(_)는 사용하지 않는다.<br>
https://ex.co.kr/classes/java/curriculums/web_master (X)
- URI 경로에는 소문자가 적합하다.<br>
https://ex.co.kr/classes/JAVA/curriculums/web-master (X)
- 파일 확장자는 URI에 포함하지 않는다.<br>
https://ex.co.kr/classes/java/curriculums/web-master.jsp (X)
- 프로그래밍 언어에 의존적인 확장자를 사용하지 않는다.<br>
https://ex.co.kr/classes/java/curriculums/web-master.do (X)
- 구현에 의존적인 경로를 사용하지 않는다.<br>
https://ex.co.kr/servlet/classes/java/curriculums/web-master (X)
- 세션 ID를 포함하지 않는다.<br>
https://ex.co.kr/classes/java/curriculums/web-master?session-id=abc (X)
- 프로그래밍 언어의 Method명을 이용하지 않는다.<br>
https://ex.co.kr/classes/java/curriculums/web-master?action=intro (X)
- 명사에 단수형보다는 복수형을 사용한다(컬렉션에 대한 표현은 복수로 사용).<br>
https://ex.co.kr/classes/java/curriculums/web-master (X)
- 컨트롤러 이름으로는 동사나 동사구를 사용한다.<br>
https://ex.co.kr/classes/java/curriculums/web-master/re-order
- 경로 부분 중 변하는 부분은 유일한 값으로 대체한다.<br>
.../curriculums/web-master/lessons/**{lesson-id}**/users/**{user-id}**<br>
.../curriculums/web-master/lessons/**2**/users/**100**
- CRUD 기능을 나타내는 것은 URI에 사용하지 않는다.<br>
GET: .../curriculums/web-master/lessons/2/users/100/**READ** (X)<br>
DELETE: .../curriculums/web-master/lessons/2/users/100 (O)
- URI Query Parameter 디자인: URI 쿼리 부분으로 컬렉션 결과에 대해 필터링할 수 있다.<br>
.../curriculums/web-master?**chpater=2**
- URI 쿼리는 컬렉션의 결과를 페이지로 구분하여 나타내는 데 사용한다.<br>
.../curriculums/web-master?**chapter=2&page=0&size=10&sort=asc**
- API에 있어서 서브 도메인은 일관성있게 사용해야 한다.<br>
https://ex.co.kr<br>
https://api.ex.co.kr<br>
https://api-ex.co.kr
- 클라이언트 개발자 포탈 서브 도메인은 일관성있게 만든다.<br>
https://dev-ex.co.kr<br>
https://developer-ex.co.kr
</details>
<br>

### HTTP
<details>
<summary><b>HTTP(Hyper Text Trasfer Protocol)</b></summary>

RFC-2616에서 규정된 Web에서 데이터를 주고받는 프로토콜이다. 이름은 하이퍼텍스트 전송용 프로토콜로 정의되어 있지만 실제로는 HTML, XML, JSON, Image, Voice, Video, Javascript, PDF 등 다양한 컴퓨터에서 다룰 수 있는 것은 모두 전송할 수 있다. TCP를 기반으로 한 REST의 특징을 모두 구현하고 있는 Web기반의 프로토콜로 메세지를 주고(Request) 받는(Response) 형태의 통신 방법이다.
</details>
<details>
<summary><b>HTTP 요청 Method</b></summary>

REST를 구현하기 위한 인터페이스
|   |의미|CRUD|멱등성|안정성|Path Variable|Query Parameter|DataBody|
|:-:|-|:-:|:-:|:-:|:-:|:-:|:-:|
|**GET**|리소스 취득|R|O|O|O|O|X|
|**POST**|리소스 생성, 주가|C|X|X|O|△|O|
|**PUT**|리소스 갱신, 생성|C/U|O|X|O|△|O|
|**DELETE**|리소스 삭제|D|O|X|O|O|X|
|**HEAD**|헤더 데이터 취득|-|O|O|-|-|-|
|**OPTIONS**|지원하는 메소드 취득|-|O|-|-|-|-|
|**TRACE**|요청메세지 반환|-|O|-|-|-|-|
|**CONNECT**|프록시 동작의 터널 접속으로 변경|-|X|-|-|-|-|
</details>
<details>
<summary><b>HTTP Status Code</b></summary>

응답의 상태를 나타내는 코드
|코드|의미|내용|
|:-:|:-:|-|
|**1XX**|처리중|처리가 계속되고 있는 상태. 클라이언트는 요청을 계속하거나 서버의 지시에 따라서 재요청|
|**2XX**|성공|요청의 성공|
|200|성공|성공|
|201|성공|리소스 생성 성공|
|**3XX**|리다이렉트|다른 리소스로 리다이렉트. 해당 코드를 받았을 때는 Response의 새로운 주소로 다시 요청|
|301|리다이렉트|리소스가 다른 장소로 변경됨을 알림|
|303|리다이렉트|클라이언트에서 자동으로 새로운 리소스로 요청 처리|
|**4XX**|클라이언트 에러|클라이언트의 요청에 에러가 있는 상태. 재전송해도 에러가 해결되지 않음|
|400|클라이언트 에러|요청 오류, 파라미터 에러|
|401|클라이언트 에러|권한 없음(인증 실패)|
|404|클라이언트 에러|리소스 없음(페이지를 찾을 수 없음)|
|**5XX**|서버 에러|서버 처리중 에러가 발생한 상태. 재전송시 에러가 해결될 수도 있음|
|500|서버 에러|서버 내부 에러(서버 동작 처리 에러)|
|503|서버 에러|서비스 정지(점검 등)|
</details>
<br>
<br>

## Spring

<details>
<summary><b>Spring이란?</b></summary>

- Spring 1.0 버전은 2004년 3월 출시되었으며, 지난 20년 가까이의 세월 동안 자바 엔터프라이즈 어플리케이션 개발의 최고의 자리를 차지했다.
- 스프링 프레임워크는 20여 가지의 모듈로로 구성되어 있고, 이러한 모듈들은 스프링의 핵심 기능(DI, AOP 등)을 제공해주며 필요한 모듈만 선택하여 사용 가능하다.
- 현재 단일 아키텍쳐(모놀리스) 마이크로 서비스 아키텍쳐로 변환 중이며 여기에 맞춰 스프링도 진화하고 있는 상태이다.
- 여러가지 모듈이 있지만 그 중 스프링부트, 스프링클라우드, 스프링데이터, 스프링배치, 스프링시큐리티에 중점을 둔다.
- 스프링은 **테스트의 용이성**, **느슨한 결합**에 중점을 두고 개발한다.
- 2000년대 초의 자바 EE 어플리케이션은 작성, 테스트가 매우 어려웠으며 한 번 테스트 하기가 번거로웠다. 이로 인하여 느슨한 결합이 된 어플리케이션 개발이 힘든 상태였으며, 특히 데이터베이스와 같이 외부에 의존성을 두는 경우 단위테스트가 불가능했다.
- 스프링과 다른 프레임워크의 가장 큰 차이점은 IoC를 통한 개발의 진행이다.
- AOP를 사용하여 로깅, 트랜잭션 관리, 시큐리티에서의 적용 등 AspectJ와 같이 완벽하게 구현된 AOP와 통합하여 사용 가능하다.
</details>
<details>
<summary><b>Spring POJO</b></summary>

- **IoC / DI** : 의존 관계 주입
- **AOP** : 관점 중심 프로그램
- **PSA** : 이식 가능한 추상화
</details>
<br>

### IoC와 DI
<details>
<summary><b>IoC(Inversion of Control)</b></summary>

스프링에서는 일반적인 자바 객체를 new로 생성하여 개발자가 관리하는 것이 아닌 Spring Container에게 모두 맡긴다. 즉, 개발자에서 프레임워크로 제어의 객체 관리 권한이 넘어가며 이를 **제어의 역전**이라 한다.
</details>
<details>
<summary><b>DI(Dependency Injection)</b></summary>

**장점**
- 의존성으로부터 격리시켜 코드 테스트에 용이하다.
- DI로 불가능한 상황을 Mock과 같은 기술을 통하여 안정적으로 테스트 가능하다.
- 코드를 확장하거나 변경할 때 영향을 최소화한다(추상화).
- 순환 참조를 막을 수 있다.
</details>
<br>

### AOP
<details>
<summary><b>AOP(Aspect Oriented Programming)</b></summary>

관점지향 프로그램을 의미한다. 스프링 어플리케이션은 대부분 특별한 경우를 제외하고는 MVC 웹 어플리케이션에서 Web Layer, Business Layer, Data Layer로 정의한다.
- Web Layer: REST API를 제공하며, Client 중심의 로직 적용
- Business Layer: 내부 정책에 따른 logic과 해당 부분 개발
- Data Layer: 데이터베이스 및 외부와의 연동 처리
</details>
<details>
<summary><b>주요 Annotation</b></summary>

|Annotation|Explanation|
|:-:|-|
|@Aspect|자바에서 널리 사용하는 AOP 프레임워크에 포함되며, AOP를 정의하는 클래스에 할당|
|@Pointcut|method, annotation 등 AOP를 적용 시킬 지점을 설정|
|@Before|메소드 실행 이전|
|@After|메소드 성공적으로 실행 후. 예외가 발생하더라도 실행|
|@AfterReturing|메소드 호출 성공 실행 시 (Not Throws)|
|@AfterThrowing|메소드 호출 실패 예외 발생 (Throws)|
|@Around|Before/After 모두 제어|
</details>
<br>

### 여러 가지 Annotation
<details>
<summary><b>Click하여 보기</b></summary>

|Annotation|Explanation|
|:-:|-|
|@SpringBootApplication|Spring boot application으로 설정|
|@Controller|View를 제공하는 controller로 설정|
|@RestController|REST API를 제공하는 controller로 설정|
|@RequestMapping|URL 주소 맵핑|
|@GetMapping|Http GetMethod URL 주소 맵핑|
|@PostMapping|Http PostMethod URL 주소 맵핑|
|@PutMapping|Http PutMethod URL 주소 맵핑|
|@DeleteMapping|Http DeleteMethod URL 주소 맵핑|
|@RequestParam|URL Query Parameter 맵핑|
|@RequestBody|Http Body를 Parsing 맵핑|
|@Valid|POJO Java class의 검증|
|@Configration|1개 이상의 bean을 등록할 때 설정|
|@Component|1개의 class 단위로 등록할 때 사용|
|@Bean|1개의 외부 library로부터 생성한 객체를 등록할 때 사용|
|@Autowired|DI를 위한 곳에 사용|
|@Qualifier|@Autowired 사용시 bean이 2개 이상일 때 명시적 사용|
|@Resource|@Autowired + @Qualifier의 개념으로 이해|
|@Aspect|AOP 적용시 사용|
|@Before|AOP 메소드 이전 호출 지정|
|@After|AOP 메소드 호출 이후 지정 예외 발생 포함|
|@Around|AOP 이전/이후 모두 포함 예외 발생 포함|
|@AfterReturning|AOP 메소드의 호출이 정상일 때 실행|
|@AfterThrowing|AOP 해당 메소드가 예외 발생시 지정|
</details>
<br><br>

## Spring Boot

<details>
<summary><b>Spring Boot</b></summary>

- 스프링부트는 단순히 실행되며, 프로덕션 제품 수준의 스프링 기반 어플리케이션을 쉽게 만들 수 있다.
- 스프링부트 어플리케이션에는 스프링 구성이 거의 필요하지 않다.
- 스프링부트 java -jar로 실행하는 자바 어플리케이션을 만들 수 있다.
</details>
<details>
<summary><b>주요 목표</b></summary>

- 스프링 개발에 대해 빠르고 광범위하게 적용할 수 있는 환경
- 기본값 설정이 있지만 설정을 바꿀 수 있음
- 대규모 프로젝트에 공통적인 비기능 제공 (보안, 모니터링 등)
- XML 구성 요구사항이 전혀 없음
</details>
<details>
<summary><b>장점</b></summary>

- 어플리케이션 개발에 필수 요소들만 모아두었다.
- 간단한 설정으로 개발 및 커스텀이 가능하다.
- 간단하고 빠르게 어플리케이션 실행 및 배포가 가능하다.
- 대규모 프로젝트(운영환경)에 필요한 비 기능적 기능도 제공한다.
- 오랜 경험에서 나오는 안정적인 운영이 가능하다.
- 스프링에서 불편한 설정(XML 설정 등)이 없어졌다.
</details>
<br>

### REST API 관련 Annotation
<details>
<summary><b>GET API</b></summary>

|   |의미|CRUD|멱등성|안정성|Path Variable|Query Parameter|DataBody|
|:-:|-|:-:|:-:|:-:|:-:|:-:|:-:|
|**GET**|리소스 취득|R|O|O|O|O|X|

|Annotation|Explanation|
|:-:|-|
|@RestController|Rest API 설정|
|@RequestMapping|리소스 설정(method로 구분 가능)|
|@GetMapping|Get Resource 설정|
|@RequestParam|URL Query Param Parsing|
|@PathVariable|URL Path Variable Parsing|
|Object|Query Param Object로 Parsing|
</details>
<details>
<summary><b>POST API</b></summary>

|   |의미|CRUD|멱등성|안정성|Path Variable|Query Parameter|DataBody|
|:-:|-|:-:|:-:|:-:|:-:|:-:|:-:|
|**POST**|리소스 생성, 주가|C|X|X|O|△|O|

|Annotation|Explanation|
|:-:|-|
|@RestController|Rest API 설정|
|@RequestMapping|리소스 설정(method로 구분 가능)|
|@PostMapping|Post Resource 설정|
|@RequestBody|Request Body 부분 Parsing|
|@PathVariable|URL Path Variable Parsing|
|@JsonProperty|json naming|
|@JsonNaming|class json naming|
</details>
<details>
<summary><b>PUT API</b></summary>

|   |의미|CRUD|멱등성|안정성|Path Variable|Query Parameter|DataBody|
|:-:|-|:-:|:-:|:-:|:-:|:-:|:-:|
|**PUT**|리소스 갱신, 생성|C/U|O|X|O|△|O|

|Annotation|Explanation|
|:-:|-|
|@RestController|Rest API 설정|
|@RequestMapping|리소스 설정(method로 구분 가능)|
|@PutMapping|Put Resource 설정|
|@RequestBody|Request Body 부분 Parsing|
|@PathVariable|URL Path Variable Parsing|
</details>
<details>
<summary><b>DELETE API</b></summary>

|   |의미|CRUD|멱등성|안정성|Path Variable|Query Parameter|DataBody|
|:-:|-|:-:|:-:|:-:|:-:|:-:|:-:|
|**DELETE**|리소스 삭제|D|O|X|O|O|X|

|Annotation|Explanation|
|:-:|-|
|@RestController|Rest API 설정|
|@RequestMapping|리소스 설정(method로 구분 가능)|
|@DeleteMapping|Delete Resource 설정|
|@RequestParam|URL Query Param Parsing|
|@PathVariable|URL Path Variable Parsing|
|Object|Query Param Object로 Parsing|
</details>
<br>

### Response 관련 Class 및 Annotation
<details>
<summary><b>Click하여 보기</b></summary>

|Class/Annotation|Explanation|
|:-:|-|
|String|일반 Text Type 응답|
|Object|자동으로 Json 변환되어 응답 상태값은 항상 200 OK|
|ResponseEntity|Body의 내용을 Object로 설정. 상황에 따라서 HTTP Status Code 설정|
|@ResponseBody|RestController가 아닌 곳(Controller)에서 Json 응답을 내릴 때|
</details>
<br><br>

## Spring Boot 기능 활용

### Validation
<details>
<summary><b>Validation이란?</b></summary>

Validation은 프로그래밍에 있어서 가장 필요한 부분이다. 특히 자바에서는 null 값에 대해서 접근하려고 할 때 null pointer exception이 발생하므로, 이러한 부분을 방지하기 위해서 미리 검증하는 과정을 Validation이라고 한다.
</details>
<details>
<summary><b>특징</b></summary>

- 검증해야할 값이 많은 경우 코드의 길이가 길어진다.
- Service Logic과의 분리가 필요하다.
- 흩어져 있는 경우, 어디에서 검증을 하는지 알기 어렵고 재사용의 한계가 있다.
- 검증 Logic이 변경되는 경우, 테스트 코드 등 참조하는 클래스에서 Logic이 변경되어야 하는 부분이 발생할 수 있다.
</details>
<details>
<summary><b>관련 Annotation</b></summary>

|Annotation|Explanation|
|:-:|-|
|@Size|문자 길이 측정|
|@NotNull|null 불가|
|@NotEmpty|null, "" 불가|
|@NotBlank|null, "", " " 불가|
|@Past|과거 날짜|
|@PastOrPresent|오늘 또는 과거 날짜|
|@Future|미래 날짜|
|@FutureOrPresent|오늘 또는 미래 날짜|
|@Pattern|정규식 적용|
|@Max|최댓값|
|@Min|최솟값|
|@AssertTrue / False|별도 Logic 적용|
|@Valid|해당 object validation 실행|
</details>
<details>
<summary><b>Custom Validation</b></summary>

- AssertTrue / False와 같은 method 지정을 통해서 Custom Logic 적용 가능
- ConstraintValidator를 적용하여 재사용이 가능한 Custom Logic 적용 가능
</details>
<details>
<summary><b>etc</b></summary>

- **gradle dependecies**   
implementation("org.springframework.boot:spring-boot-starter-validation")
- **bean validation spec**   
https://beanvalidation.org/2.0-jsr380
</details>
<br>

### Exception
<details>
<summary><b>Web이 에러를 표현하는 방법</b></summary>

- 에러 페이지
- 4XX or 5XX 에러
- Client가 200 외에 처리를 하지 못할 때는 200을 내려주고 별도의 에러 메세지 전달
</details>
<details>
<summary><b>관련 Annotation</b></summary>

|Annotation|Explanation|
|:-:|-|
|@ControllerAdvice|Global 예외 처리 및 특정 package/Controller 예외 처리|
|@ExceptionHandler|특정 Contrller의 예외 처리|
</details>
<br>

### Filter
<details>
<summary><b>Filter란?</b></summary>
Web Application에서 관리되는 영역으로 스프링부트 프레임워크에서 클라이언트로부터 오는 요청/응답에 대해 최초/최종 단계의 위치에 존재하며, 이를 통해서 요청/응답의 정보를 변경하거나 스프링에 의해서 데이터가 변환되기 전의 순수한 클라이언트의 요청/응답 값을 확인할 수 있다.
유일하게 ServletRequest, ServletResponse의 객체를 변환할 수 있다. 주로 스프링 프레임워크에서는 요청/응답의 logging 용도로 활용하거나 인증과 관련된 logic 들을 해당 Filter에서 처리한다. 이를 선/후 처리 함으로써 Service Business Logic과 분리한다.
</details>
<br>

### Interceptor
<details>
<summary><b>Interceptor란?</b></summary>
Filter와 매우 유사한 형태로 존재하지만 Spring Context에 등록된다는 차이점이 있다. AOP와 유사한 기능을 제공할 수 있으며, 주로 인증단계를 처리하거나, logging을 하는 데에 사용한다. 이를 선/후 처리 함으로써 Service Business Logic과 분리한다.
</details>
<br>

### JUnit Test
<details>
<summary><b>TDD(Test-driven Development)</b></summary>
테스트 주도 개발에서 사용하지만, 코드의 유지 보수 및 운영 환경에서의 에러를 미리 방지하기 위해 단위 별로 검증하는 테스트 프레임워크이다.
</details>
<details>
<summary><b>단위테스트</b></summary>
작성한 코드가 기대하는 대로 동작을 하는지 검증하는 절차이다.
</details>
<details>
<summary><b>JUnit</b></summary>
자바 기반의 단위 테스트를 위한 프레임워크로, Annotation 기반으로 테스트를 지원하며, Assert로 (예상, 실제)를 통해 검증한다.
</details>
<details>
<summary><b>Jacoco</b></summary>
자바 코드의 코드 커버리지를 체크하는 라이브러리이며, html, xml, csv로 결과 확인 가능하다.
</details>
<br>

### Swagger
<details>
<summary><b>Swagger란?</b></summary>

개발한 REST API를 편리하게 문서화해주고 이를 통해서 관리 및 제 3의 사용자가 편리하게 API를 호출해보고 테스트할 수 있는 프로젝트이다. Spring Boot에서는 간단하게 springfox-boot-starter를 gradle dependencies에 추가하여 사용할 수 있다. 다만, 운영환경과 같은 외부에 노출되면 안되는 곳에 사용할 때는 주의해야 한다.
</details>
<details>
<summary><b>관련 Annotation</b></summary>

|Annotation|Explanation|
|:-:|-|
|@Api|클래스를 스웨거의 리소스로 표시|
|@ApiOperation|특정 경로의 오퍼레이션 HTTP 메소드 설명|
|@ApiParam|오퍼레이션 파라미터에 메타 데이터 설명|
|@ApiResponse|오퍼레이션의 응답 지정|
|@ApiModelProperty|모델의 속성 데이터 설명|
|@ApiImplicitParam|메소드 단위의 오퍼레이션 파라미터 설명|
|@ApiImplicitParams||
</details>
<br>
