# How java works? - CUK GDSC

> **“Write Once, Run Anywhere”  - 플랫폼 독립적인 자바의 철학**
> 

# 저자

CUK GDSC Team.Java

java team 이승원  장주은 정승원 최민수 한준희

# 서문

2024년 현재 한국취업 시장에서 대학생이 압도적으로 많다. 이는 대학생활만으로 취업하기 어렵다는것을 반증한다. 그러므로, 취업을 위하여 정보처리기사, sqld등의 기사 자격증은 필수적이다.

참고자료로 한국산업인력공단이 운영하는 큐넷의 2022년 기사 자격증 시험 응시자 정보이다.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/54ed90c0-2813-4ba4-b184-41ea433c61cf/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/8d48c27d-742a-4333-867d-9788825971da/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/3e3bf629-718a-4b9d-b37f-b6cf54978d43/Untitled.png)

다음은 국비지원 부트캠프의 일반적인 자바 교육과정이다. 부트캠프는 일반적으로 6개월 간의 과정이므로 자바에 관한 심도있는 이해를 바라기는 어렵다.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/f12289dc-a345-4977-adad-95490ddced32/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/1deafa2d-23a4-4365-a50d-1d75d1e3d85e/Untitled.png)

따라서, 우리는 자바의 JVM에 대한 이해를 높이고자 이 문서를 작성한다. 

# 들어가기 전 - JDK/JRE/JVM

![스크린샷 2024-06-30 124447.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/dd10ce7f-04f0-4a68-be7f-b3e4cfeca40b/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2024-06-30_124447.png)

**`JDK(Java Development Kit)`**: 자바 개발 환경으로 자바 어플리케이션을 개발하기 위해 필요한 도구를 제공(javac, javap 등..) JDK는 JRE + 개발 도구라고 볼 수 있다.

**`JRE(Java Runtime Environment)`**: 자바를 실행하기 위한 환경이며, JVM, 자바 클래스 라이브러리, 기타 실행용 파일을 포함

**`JVM(Java Virtual Machine)`**: 자바 가상 머신

- 자바 프로그램을 실행하기 위한 가상 머신
- 운영체제에 종속되지 않게 자바 프로그램을 실행할 수 있게 해줌
- 물론 JVM자체는 운영체제 종속적(운영체제에 맞춰 설치해야 함)

<aside>
💡 **# 용어정리**
**javac** : java compiler 자바 컴파일러로서 자바 소스 파일을 자바 바이트 코드 파일로 변환
**javap** : 자바 바이트 코드 파일을 사람이 읽기 쉬운 형태로 역어셈블링 해주는 프로그램

</aside>

# 0. 자바 프로그램의 동작 과정

![Screenshot 2024-06-30 at 10.23.22.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/94435071-cd4b-4b87-9122-bdbd2769ec35/Screenshot_2024-06-30_at_10.23.22.png)

해당 그림으로 전체적인 상황을 파악하며 밑의 자세한 내용을 확인하면 된다.

# 1. 컴파일 (javac)

런타임 이전(컴파일 타임)에 자바 소스 코드(.java)를 컴파일러(javac)를 통해 바이트(.class)코드로 변환하는 과정

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/46d24ced-a27a-4394-8b36-0e82c116a8f0/Untitled.png)

위 사진이 바로 바이트 코드이다. 바이트 코드는 자체는 바이너리 파일이다. 즉 인간이 파악하기 어려운 이진수로 구성되어 있다. 왼쪽에 offset 8비트(1바이트)가 명령어이다. 명령어가 256(2^8)개를 모두 사용하지는 않지만,  총 1바이트를 사용하기에 바이트코드라고 부른다. 그외에 오른쪽 16바이트는 명령어로 조작할 대상의 포인터나 데이터를 담는다. 바이트 코드는 symbolic reference를 사용한다.

<aside>
💡 **# Symbolic Reference vs Direct Reference**
Symbolic Reference : 심볼릭 참조는 참조값을 우리가 작성하면서 사용한 class, field, method의 이름을 참조로 사용하는 것을 말한다.
Direct Reference : 직접 참조는 참조값을 실제 물리 메모리주소로 사용하는 것은 말한다. ex) c의 포인터

</aside>

<aside>
💡 **# 기계어 vs 어셈블리어**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/eb0d5655-6430-4427-a045-9fab19d8d735/Untitled.png)

**기계어**: 기계가 직접 이해할 수 있는 이진수를 의미한다. 또한 하드웨어에 종속적인 것이 특징이다. (즉 CPU 명령어 체계에 따라 달라진다)

**어셈블리어**: 기계어는 이진수로 되어있기에 인간이 보기에 어렵다. 이를 극복하고자 인간이 읽고 쓰기 쉽도록 1대1 대응하는 언어로 작성한 것이 어셈블리어다. 기계어와 1대1 대응하기에 마찬가지로 하드웨어 종속적이다. 이를 기계어로 번역해주는 것을 어셈블러라고 한다.

**그렇다면 자바 바이트코드는 어느쪽일까?**

CPU가 직접 알아들을 수 없기에 기계어는 아니며, 어셈블리어에 가깝다고 볼 수 있다. 그러나 자바 바이트 코드는 자바 철학에 따라 하드웨어 종속적이지 않음을 기억해야한다.

</aside>

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/9a427d02-0d02-4e61-80fb-086f8cd6cfb4/Untitled.png)

만약 바이트코드를 역어셈블러(javap)로 해석해서 보면 이런식으로 볼 수 있다.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/b563ef10-4edf-407a-bd12-55eb71784a5a/Untitled.png)

인텔리제이와 같은 IDE에서도 .class파일을 열면 이런식으로 역컴파일된 파일을 보여주는데, 알아두어야 할 것은 실제 .class파일은 위에서 보았듯 바이너리 파일로 완전히 다르게 생겼다. (바이트 코드가 저렇게 생겼다고 착각하지 말 것!)

# 2. 클래스 로딩(Class Loading)

JVM이 컴파일 된 바이트 코드를 읽고 메모리에 로드를 수행하는 과정

즉 자바 프로그램을 실행하기 위해 필요한 클래스와 객체들을 메모리(Run Time Data Area)에 옮기는 것이다.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/143fedc8-6827-4cdb-aedd-bc6981f4536f/Untitled.png)

클래스 로더는 크게 3가지로 역할을 맡는다.

Loading: 클래스 파일을 탑재

Linking: 클래스 파일을 사용하기 위해 검증 + 기본값으로 초기화

Initailization: 정적(static) 필드의 값들을 코드 상에서 정의한 값으로 초기화

## **클래스 로더의 특징(Class Loader’s feature)**

![방식.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/1e9e394c-8fd3-4d5f-9fe7-75ea31613d3d/%EB%B0%A9%EC%8B%9D.png)

- **계층적 (Hierarchical)**
    
    코드를 구현하다 보면 중복을 줄이기 위해 상속을 사용하게 된다.
    
    부모 Class를 가진 자식 Class처럼 ClassLoader도 계층적으로 생성이 가능하다.
    
    클래스 로더는 아래와 같은 계층 구조를 가지고 있다.
    

![1.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/76725efa-c365-4f75-b9f5-b98b18aed23e/1.png)

- **가시성 (Visibility)**
    
    A class 가 상위 ClassLoader이고 B와 C라는 class가 하위 ClassLoader
    
    A class는 부모이므로 B와 C의 데이터 사용X
    
    같은 부모를 가진 B와 C 서로 데이터 사용X
    
    B와 C는 부모 A의 데이터 사용O
    
    ![클래스로딩1.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/3655d356-98bf-498a-afe7-d52f88a39a55/%ED%81%B4%EB%9E%98%EC%8A%A4%EB%A1%9C%EB%94%A91.png)
    
- **위임형 로드 요청 (Delegation)**

      ClassLoader1의 자식 = ClassLoader2

ClassLoader2의 자식 = ClassLoader3

부모 클래스가 우선권을 가지고 있으므로 ClassLoader3 → ClassLoader2 → ClassLoader1 순서로 요청 가능

- **언로드 불가 (Unload Impossibility)**
    
    ClassLoader에는 Class 언로딩(Unloading) 기능이 없다.
    
    그렇기에 언로딩(Unloading)을 하기 위해선 ClassLoader 자체를 삭제하고, ClassLoader을 다시 생성하는 방법이 있다.
    

## ClassLoader의 역할

![역할.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/de35e803-1d62-4b11-ba4f-83cd4323b538/%EC%97%AD%ED%95%A0.png)

- **부트스트랩 클래스 로더**: JVM을 기동할 때 생성되며, Object 클래스들을 비롯하여 자바 API들을 로드한다. 다른 클래스 로더와 달리 자바가 아니라 네이티브 코드로 구현되어 있다.
- **익스텐션 클래스 로더(Extension Class Loader)**: 기본 자바 API를 제외한 확장 클래스들을 로드한다. 다양한 보안 확장 기능 등을 여기에서 로드하게 된다.
- **시스템 클래스 로더(System Class Loader)**: 부트스트랩 클래스 로더와 익스텐션 클래스 로더가 JVM 자체의 구성 요소들을 로드하는 것이라 한다면, 시스템 클래스 로더는 애플리케이션의 클래스들을 로드한다고 할 수 있다. 사용자가 지정한 $CLASSPATH 내의 클래스들을 로드한다.
- **사용자 정의 클래스 로더(User-Defined Class Loader)**: 애플리케이션 사용자가 직접 코드 상에서 생성해서 사용하는 클래스 로더이다.

# 3. Run Time Data Area(런타임 데이터 영역)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/b5111a09-48bf-499f-b652-bb8fdcabf8a8/Untitled.png)

- Heap Area: JVM당 하나만 존재(JVM과 생명주기를 함께함)하며 모든 스레드가 공유. Java로 구성된 객체와 JRE 클래스 들이 올라감. 문자열에 대한 정보를 가진 String Pool, 실제 데이터를 가진 인스턴스, 배열등이 여기에 저장. 해당 영역이 가진 데이터는 모든 JVM 스택 영역(위 그림에서 Stack)에서 참조되어 스레드 사이에 공유.
- String Constant Pool: Java String은 불변객체로써 여기에 생성된 문자열을 저장하고 같은 값이면 공유함

- Method Area(자바 8부터는 Meta space):  JVM당 하나만 존재(JVM과 생명주기를 함께함)하며 스레드가 모두 공유. 단. 영역자체는 JVM과 생명주기를 함께하지면 Class들은 동적으로 클래스 로더에 의해 로딩되고 초기화 됌. 인스턴스 생성을 위한 객체 구조, 생성자, 필드 등이 저장, 런타임 상수풀과 정적(static)변수, 메서드 데이터와 같은 클래스 데이터가 여기에 저장됌.
- Class Constant Pool: 클래스 파일의 상수(static) 값이 저장되는 곳. 컴파일 타임에 생성됌. 심볼릭 참조를 사용하며 컴파일 타임에 바이트코드에 기록됌.
- Runtime Constant Pool (클래스와 생명주기를 함께함)
    - Class Constant Pool에 저장되어 있던 값이 런타임 시 이 영역으로 옮겨짐 이후 동적으로 관리됌
    - 각 클래스, 인터페이스의 상수 외에도 메서드와 필드에 대한 모든 래퍼런스 정보를 가지고 있음.
    - 클래스는 클래스 로드를 하는 과정에 의해 실제 직접 참조 값(물리 메모리 값)이 생기는데 기존의 Class Constant Pool의 심볼릭 참조를 직접 참조로 변역해둠.

(Tread와 생명주기를 함께 함)

- PC Resgister: 프로그램 카운터 레지스터로서 현재 실행중인 명령어의 주소가 기록된다(실제 물리주소)
- Native Method Stack: 자바로 작성된 프로그램 실행시 순수하게 자바로만 구성된 코드를 사용할 수 없는 시스템의 자원이나 API가 존재함. 이런 다른 언어로 작성된 메서드들을 Native Method라고 한다. 이런 Native Method가 사용하는 스택
- Stack: JVM Stack이라고 하기도 하며 메서드가 호출 될때마다 Frame들을 저장하는 일종의 function call stack 메서드가 완료되면 프레임이 pop됌.
- Frame(메서드와 주기를 함께함)
    - 실행중인 메서드가 속한 클래스의 로컬 변수 배열, 피연산자 스택, 런타임 상수풀에 대한 참조를 가지고 있음. (로컬 변수배열은 메서드 안의 지역변수들을 담은 것.  피연산자 스택은 메서드 내 연산을 위해서 바이트 코드 명령문이 들어있는 공간.)

# 4. 바이트 코드 해석 및 실행

- JVM의 바이트 코드를 해석해서 기계어로 변환해 실행하는 과정.
- 기본적으로 Execution Engine(실행엔진)의 인터프리터와 JIT컴파일러가 수행하며 Native 코드의 경우 Native Method Interface, Native Method Libarary가 수행하게 됌
- 인터프리터와 컴파일러의 장단점
    - 인터프리터는 명령어를 하나씩 읽고 해석하기에 하나 하나의 명령어에 대한 해석은 빠르지만, 반복해서 명령어가 나오면 계속 번역하기에 컴파일러보다 상대적으로 느림
    - 컴파일러는 모든 코드 내용을 알고 번역하기에 여러가지 최적화가 가능. 따라서 컴파일 타임이 따로 필요하지만 빠름.

<aside>
💡 **# 용어정리
인터프리터**: 코드 명령어를 하나씩 읽어서 해석하고 실행 (JVM의 기본 해석 방법)

**컴파일러** : 코드파일 전체를 읽고 한번에 해석된 파일을 내놓는 방법

**JIT(Just-In-Time) 컴파일러**: 인터프리터의 단점을 보완하고자 자주 실행하는 명령어(HotSpot이라는 표현을 씀)인 경우 실시간으로 컴파일을 추가 진행해 미리 기계어로 바꿔줌 (JVM의 속도향상을 위한 보조 해석 방법)

</aside>

# 5. 가비지 컬렉터(GC, Garbage Collector)

자바의 JVM에서는 **가비지 컬렉터가** 불필요한 메모리를 알아서 정리해주어 메모리 누수를 방지해주고 메모리를 청소해준다.

동작 과정

1. Stop The World : 가비지 컬렉션을 실행하기 위해 **JVM이 애플리케이션의 실행을 멈추는 작업**으로 **GC를 실행하는 쓰레드를 제외한 모든 쓰레드들의 작업이 중단**되고, GC가 완료되면 작업이 재개된다.
2. Mark, Sweep and Compacting
    - Mark : 사용되는 메모리와 사용되지 않는 **메모리를 식별**하는 작업
    - Sweep : Mark 단계에서 사용되지 않음으로 **식별된 메모리를 해제**하는 작업
    - Compacting : 메모리 단편화를 해결하는 작업

<aside>
💡 **# 메모리 단편화란?**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/5adc2613-15c4-49bb-8729-1b19b6884ace/d3e7c06a-d86c-4f9c-950f-8551111538a8/Untitled.png)

위 이미지와 같이 메모리를 사용 후 해제하게 되면 메모리 사이에 빈 공간이 생기게 된다. 이렇게 되면 총 12K의 여유 메모리가 있음에도 5K가 넘는 작업은 실행 할 수 없다. 이런 현상을 메모리 단편화라고 한다. 이를 해결하기 위해서는 사용중인 메모리를 연속으로 모으고 나머지 공간을 온전히 사용할 수 있도록 해주어야 한다.

</aside>

# 6. JVM 최적화

- JVM은 원래 java 프로그램을 실행하기 위해 설계되었지만, 최근에는 javascript, Python 등 여러 동적 언어를 실행하는 데도 사용됨
- **최적화** 기법
    1. JIT컴파일
        - JIT컴파일러는 바이트 코드를 실행 시점에 기계어로 변환하여 성능을 향상시킴
            - 동적 인라인닝
                - ex)짧은 메서드를 호출할 때 호출 오버헤드를 줄이기 위해 메서드 본문을 호출 지점에 직접 삽입함
            - 프로파일 기반 최적화
                - ex) 자주 실행되는 경로를 최적화 하고, 잘 실행되지 않는 경로는 최적화를 덜 함
    2. 메모리 관리 최적화
        - Generational GC : 객체의 생애 주기에 따라 나눔
            - Young Generation : 단명 객체를 빠르게 수집
            - Old Generation : 장기 생존 객체를 관리
        - Concurrent GC : 애플리케이션 실행 중에도 병렬로 가비지 컬렉션을 수행하여 애플리케이션의 중단 시간을 최소화함
    3. 네이티브 인터페이스 최적화
        - JNI를 통해 네이티브 코드와 상호작용하는 성능을 최적화
            - JNI 호출 최적화 :네이티브 메서드 호출의 오버헤드를 줄이고, 자주 호출되는 네이티브 메서드를 인라인으로 변환
            - JNI캐싱 : 네이티브 메서드와 관련된 데이터를 캐시에 저장하여 반복적인 JNI호출 성능 향상 시킴
    4. 스레드 관리 최적화
        - 스레드 관리 최적화를 통해 멀티스레드 애플리케이션의 성능 높임
            - 경량 스레드 : 경량스레드를 사용하여 스레드 생성 및 context switching의 오버헤드를 줄임
            - 스레드 풀링 : 스레드 재사용을 통해 스레드 관리 비용을 절감
    5. 메모리 관리 및 최적화
        - 메모리 관리 최적화는 동적 언어의 메모리 사용을 효율적 관리하여 성능 향상시킴
            - 메모리 풀링 : 자주 사용되는 객체 메모리를 풀에 저장하여 객체 생성 및 해제하는 오버헤드를 줄임
            - 메모리 압축 : 메모리 압축 기법을 사용하여 힙 메모리 사용을 최적화하고, 메모리 파편화를 줄임
    6. 예외처리 최적화
        - 예외 발생 시 예외처리 최적화로 성능 오버헤드를 줄임
            - 온디맨드 예외처리 : 예외가 실제로 발생할 때만 예외 처리기를 로드하고 실행하여 성능 최적화
            - 예외캐싱 : 자주 발생하는 예외를 캐시에 저장하여 빠르게 처리
    
    <aside>
    💡 **#용어정리
    최적화** : 프로그램을 더 빠르고 효율적으로 실행하기 위해 다양한 방법을 사용하는 것
    **동적 인라이닝** : 자주 호출되는 메서드를 인라인으로 변환하여 함수호출 오버헤드를 줄임
    **프로파일 기반 최적화** : 애플리케이션 실행 중에 수집된 실행 데이터를 바탕으로 최적화 수행
    **네이티브 메서드** : 자바가 아닌 다른 프로그래밍 언어로 작성된 메서드
    **JNI** : Java Native Interface
    **스레드** : 프로그램 내에서 실행되는 작은 단위의 작업
    **경량 스레드** : 운영체제의 커널이 아닌 사용자 수준에서 관리되는 스레드
    **온디맨드** : 실제로 발생할 때 처리
    
    </aside>
    
    <aside>
    💡 **#추가내용
    JIT 컴파일러** : Just In Time으로, Java 프로그램은 인터프리터 방식으로 실행되어 다른 언어보다 조금 느리기에 이를 극복하기 위해 JVM에는 JIT컴파일러가 포함되어 있음. 이는 바이트코드를 실행 시점에 기계어로 변환하여 실행 속도를 크게 향상 시킴.
    **객체의 생애 주기** : 객체가 생성되어 사용되고, 더 이상 필요 없게 되면 가비지 컬렉션에 의해 메모리에서 해제되는 전체 과정
    
    </aside>
