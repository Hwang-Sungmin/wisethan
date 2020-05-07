####  Design Pattern

#####  디자인 패턴 구조

- Context
  - 문제가 발생하는 상황을 기술
- Problem
  - 패턴이 적용되어 해결할 필요가 있는 여러 디자인 이슈들을 기술
- Solution
  - 문제를 해결하도록 설계를 구성하는 요소들과 그 요소들 사이의 관계



#####  디자인 패턴 종류

- 디자인 패턴

  - 생성(Creational), 구조(Structual), 행위(Behavioral) 3가지로 분류

     1. 생성 패턴

        - 객체 생성에 관련된 패턴
        - 객체의 생성과 조합을 캡슐화해 특정 객체가 생성되거나 변경되어도 프로그램 구조에 영향을 크게 받지 않도록 유연성을 제공한다.

     2. 구조 패턴

        - 클래스나 객체를 조합해 더 큰 구조를 만드는 패턴
        - 2개의 객체를 묶어 단일 인터페이스를 제공, 객체를 묶어 새로운 기능을 제공한다.

     3.  행위

        - 객체나 클래스 사이의 알고리즘이나 책임 분배에 관련된 패턴

        - 객체 사이의 결합도를 최소화하는 것에 중점을 둔다.

          

- GoF 디자인 패턴의 종류

  - 생성 패턴

    >  	1. 추상 팩토리 ( Abstract Factory )
    >      - 구체적인 클래스에 의존하지 않고 서로 연관되거나 의존적인 객체들의 조합을 만드는 인터페이스를 제공하는 패턴
    >  	2. 팩토리 메서드 ( Factory Method )
    >      - 객체 생성 처리를 서브 클래스로 분리해 처리하도록 캡슐화하는 패턴
    >  	3. 싱글턴 (Singleton)
    >      - 전역 변수를 사용하지 않고 객체를 하나만 생성하도록 하며, 생성된 객체를 어디에서든지 참조할 수 있도록 하는 패턴	

  -  구조 패턴

    >  	1. 컴퍼지트 ( Composite )
    >  	2. 데커레이터 ( Decorator  )

  - 행위 패턴

    >  	1. 옵져버 ( Observer )
    >      - 한 객체의 상태 변화에 따라 다른 객체의 상태도 연동되도록 1:m 객체 의존 관계를 구성하는 패턴
    >  	2. 스테이트 ( State )
    >  	3. 스트래티지 ( Strategy )
    >  	4. 템플릿 메서드 ( Template Method )
    >  	5. 커맨드 ( Command )



####  OS

- Paging

  > 프로세스를 일정 크기인 페이지로 잘라서 메모리에 적재하는 방식

  - 단편화를 해결하는 방법

  - 가상메모리를 최소 단위로 쪼개어 일정한 크기인 블럭을 페이지

  - 실제기억공간(RAM)은 페이지 크기와 같은 블럭으로 나누어 프레임

  - MMU : 주소의 영역을 정해주는 역할

    - 재배치 레지스터 : CPU에서 원하는 데이터 위치와 메모리상에 프로그램의 위치를 맞춤.

    

    < 프로그램 실행 로직 > 

    ![메모리 적재](C:\Users\WiseThan\Desktop\공부해보자!\메모리 적재.PNG)

- Scheduling 

  > 프로세스가 생서오디어 실행될때 필요한 시스템의 여러자원을 해당 프로세스에게 할당하는 작업

  - 선점 ( Preemptive )
    - 우선순위에 따라 순서가 바뀜
    - 빠른 응답 시간을 요구하는 시스템에서 사용
    - 오버헤드가 크다.
    -  RR, SRT, 선점 우선순위, 다단계 큐, 다단계 피드백큐
  - 비선점 ( Non-preemptive )
    - 다른 프로세스가 강탈할 수 없다.
    - 응답시간의 예측이 편하며, 일괄처리 방식에 적합
    - FCFS, SJF( 실행시간이 작은 것 부터 ), HIRN, 우선순위, 기한부



##### Git

- **깃 초기 설정**

##### ![git](C:\Users\WiseThan\Desktop\공부해보자!\git.PNG)

- git branch
  - 