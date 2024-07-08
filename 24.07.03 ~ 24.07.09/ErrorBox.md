## 다음 java로 구현된 프로그램을 분석하여  그 실행 결과를 쓰시오

```java
class SuperObject {
    public void draw() {
        System.out.println("A");
        draw();
    }
    
    public void paint() {
        System.out.print('B');
        draw();
    }
}

class SubObject extends SuperObject {
    public void paint() {
        super.paint();
        System.out.print('C');
        draw();
    }
    
    public void draw() {
        System.out.print('D');
    }
}

public class Test {
    public static void main(String[] args) {
        SuperObject a = new SubObject();
        a.paint();
        a.draw();
    }
}
```

### 1. SuperObject a = new SubObject();

- SuperObject 클래스의 생성자를 이용하여 SuperObject 클래스 객체 변수 a를 생성한다.

### 2. a.print();

- 클래스 형 변환이 발생하였고 print() 메소드가 자식 클래스에서 재정의되었으므로 SubObject  클래스의 paint() 메소드가 호출된다.
- 

### 2-1. class SubObject extends SuperObject {
	public void paint() {

- 반환값이 없는 paint() 메소드의 시작점이다.

### 2-2. super.paint();

- 부모 클래스를 호출하는 예약어super를 사용했으므로 부모 클래스의 paint() 메소드를 호출한다.

### 2-3. class SuperObject{
	public void paint() {
		System.out.Printf('B');

- 반환값이 없는 paint()메소드의 시작점이다.
- 화면에 B를 출력한다.

> B


### 2-4. draw();

- draw() 메소드를 호출한다. draw() 메소드는 자식 클래스에서 재정의 되었으므로 SubObject 클래스의 draw() 메소드가 반환한다.

### 2-5. public void draw() {
		system.out.print('D');

- 화면에 D를 출력합니다.

> BD
> 

### 3. System.out.print('C');
    daraw();

- paint() 메소드가 끝나기 때문에 다음 줄로 이동한다.
- 화면에 C를 출력한다.

> BDC
> 
- daraw() 메소드 호출한다.

### 4. public void draw() {
		system.out.print('D');}

- daraw() 메소드를 시작지점이다.
- 화면에 D를 출력한다.

> BDCD
> 

### 5. a.draw();

- 자식 클래스로 재정의 되었기 때문에 자식 클래스에 draw() 메소드를 호출

### 5-1. public void draw() {
		system.out.print('D');}

- 화면에 D를 출력한다.

> BDCDD
> 

## 다음 설명에 해당하는 용어를 보기에서 찾아 쓰시오

- 인터넷 애플리케이션에서 사용자 인증에 사용되는 표준 인증 방법으로, 공개 API(OpenAPI)로 구현되었다.
- 인터넷 사용자가 웹사이트나 애플리케이션에 비밀번호를 제고하지 않고 자신에게 접근 권한을 부여하여 사용할 수 있다.
- 2010년 ETF에서 1.0이 공식 표준안으로 발표되었다.

> OAuth
> 

## 분석하고 그 실행 결과를 쓰시오

```c
#include <stdio.h>
main() {
	char *p = "KOREA";
	printf("1. %s\n", p);
	printf("2. %s\n", p +1);
	printf("3. %s\n", *p);
	printf("4. %s\n", *(p + 3));
	printf("5. %s\n", *p + 4); //k + 4 = o
}
```

> KOREA
OREA
K
E
O
> 

## 리눅스 또는 유닉스에서 ‘a.txt’ 파일에 대해 다음 <처리 조건>과 같이 권한을 부여하고자 한다. <처리 조건>을 준수하여 식을 완성하시오.

<처리 조건>

- 사용자에게 읽기, 쓰기, 실행 권한을 부여한다.
- 그룹에게 읽기, 실행권한을 부여한다.
- 기타 사용자에게 실행 권한을 부여한다.
- 한 줄로 작성하고, 8진법 숫자를 이용한 명령문을 이용한다.

> chmod 751 a.txt
> 

## UML 다이어그램에 대한 다음 설명에서 괄호에 공통으로 들어갈 알맞은 용어를 쓰시오.

( )은(는) UML 정적 모델링의 하나로, 관련있는 객체들을 하나로 묶어 상위 개념으로 추상화한 것이다. 위의 그림과 같이 유스케이스나 클래스 등의 요소들을 그룹화하여 의존 관계를 표현하며, 대규모 시스템에서 주요 요소 간의 종속성을 파악하는 데 사용한다. 시스템의 구조를 간략하게 표현할 수 있고 의존 관계를 명확하게 파악할 수 있어, 불필요한 의존 관계를 제거하거나 간략화함으써 시스템의 복잡도를 낮추는 곳에도 사용할 수 있다.

> 패키지
> 

## 테스트 기법 중 다음과 같이 ‘평가 점수표’를 미리 정해 놓은 후 각 영역에 해당하는 입력값을 넣고, 예상되는 출력값이 나오는지 실제 값과 비교하는 명세 기반 테스트 기법을 <보기>에서 찾아 쓰시오

<평가 점수표>

<케이스>

| 평가점수 | 성적등급 |
| --- | --- |
| 90 ~ 100 | A |
| 80 ~ 89 | B |
| 70 ~ 79 | C |
| 0 ~ 69 | D |

| 테스트 케이스 | 1 | 2 | 3 | 4 |
| --- | --- | --- | --- | --- |
| 점수범위 | 0 ~ 69 | 70 ~ 79 | 80 ~ 89 | 90 ~ 100 |
| 입력값 | 60 | 75 | 82 | 96 |
| 예상 결과값 | D | C | B | A |
| 실제 결과값 | D | C | B | A |

> Equivalence Partition
> 

## <R> 과 <S> 테이블에 대해 <SQL문>을 실행하였을 때 나타나는 결과를 작성하시오

<R>

<S>

| A | B |
| --- | --- |
| 1 | a |
| 2 | b |
| 3 | c |

| A | B |
| --- | --- |
| 1 | a |
| 2 | b |
| 3 | c |

<SQL 문>

```sql
SELECT A FROM R //<R> 테이블의 'A'속성을 표시한다.
UNION //두 SELECT문의 조회 결과를 통합하되 중복된 행은 한 번만 출력한다.
SELECT A FROM S //<S> 테이블의 'A'속성을 표시한다.
ORDER BY A DESC //'A' 속성을 기준으로 내림차순으로 정렬한다.
```

> 정답
> 

| A |
| --- |
| 4 |
| 3 |
| 2 |
| 1 |

## 다음 C 언어로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오.

```c
#include <stdio.h>
int isPerfectNum(int num) { // i의 값을 num이 받음
	int sum = 0;
	for (int i = 1; i < num; i++) { //전달받은 인수에서 자기를 제외한 약수를 찾는 과정
		if (num % i == 0)
			sum += i; //약수를 누적하는 과정
	}
	if (num == sum) return 1; //같으면 참
	else return 0; //아니면 거짓
}
mian() {
	int r = 0;
	for(int i = 1; i <= 100; i++)
		if (isPerfectNum(i)) //돌려받는 값이 참이면 다음으로 아니면 반복문
			r += i;
		printf("%d", r);
}
```

| i | r | num | i  | sum |
| --- | --- | --- | --- | --- |
| 1 | 0 | 1 | 1 | 0 |
| 2 |  | 2 | 1 2 |  0 1 |
| 3 |  | 3 | 1 2 3 | 0 1  |
| *** | *** | ** | *** | *** |
| 6 | 6 | 6 | 1 2 3 4 5 6 | 0 1 3 6 |
- **함수 `isPerfectNum`**
    - 입력된 숫자가 완전수인지 검사합니다.
    - 완전수란 자기 자신을 제외한 모든 약수의 합이 자신과 같은 수를 말합니다.
    - 예를 들어, 6은 1, 2, 3의 합이 6이므로 완전수입니다.
- **`main` 함수 정의 및 수정**
    - `mian()`로 되어 있는 부분을 `main()`으로 수정합니다.
    - 들여쓰기를 통일하여 가독성을 향상시킵니다.
- **결과를 출력**
    - `1`부터 `100`까지의 완전수를 찾아 그 합을 출력합니다.
    

## 네트워크에 대한 다음 설명에 해당하는 용어를 쓰시오

- 우리말로 번역하면 ‘네트워크 주소 변환’이라는 의미의 영문 3글자 약자이다.
- 1개의 정식 IP 주소에 다량의 가상 사설 IP 주소를 할당 및 연결하는 방식이다.
- 1개의 IP 주소를 사용해서 외부에 접속할 수 있는 노드가 어느 시점에 1개로 제한되는 문제가 있으나, 이때는 IP 마스커레이드를 이용하면 된다.

> NAT
> 

## 다음 설명에 해당하는 프로토콜을 쓰시오

- 자료를 일정한 크기로 정하여 순서대로 전송하는 자료의 전송방식으로, 셀이라 부르는 53Byte의 고정 길이 패킷을 이용하여 처리가 단순하고 고속망에 적합하다.
- 또한 연속적으로 셀을 보낼 때 다중화를 하지 않고 셀 단위로 동기가 이루어지지만 경우에 따라 동기식 시간 분할 다중화를 사용하기도 한다.
- CBR, VBR의 처리가 가능하며, B-ISDN과 결합하여 서비스를 제공하기도 한다.

> ATM, 비동기 전송 방식, Asynchronoous Transfer Mode
> 

## 다음은 오류가 발생하는JAVA프로그램이다. 프로그램을 분석하여 오류가 발생하는 라인을 쓰시오

```java
Class Person {
	private String name;
	public Person(String val) {
		name = val;
	}
	public static String get() {
		return name;
	}
	public void print() {
		Ststem.out.println(name);
	}
}
public class Test {
	public static void main(String[] agrs) {
		person obj = new Person("KIM");
		obj.print();
	}
}
```

- main() 메소드가 아닌 다른 메소드에 접근하기 위해서는 클래스를 메모리에 할당하는 , 즉 객체 변수를 선언하는 과정이 필요합니다.
- 반면 static으로 선언된 메소드는 객체 변수를 선언하지 않아도 클래스명을 사용해서 Person.get()과 같은 형태로 접근할 수 있습니다. 즉 static으로 선언된 메소드는 메모리에 클래스를 위한 공간이 할당되지 않았다는 것을 의미합니다.
- 그러므로 static으로 선언된 메소드에서 메모리에 존재하지도 않은 클래스의 변수 name을 참조하는 것은 불가능합니다.
- 

> 7
> 

## 접근 통제 (Access Control)에 대한 다음 설명에서 알맞은 용어를 보기에 찾아 쓰시오

[   ]

- 주체와 객체의 등급을 비교하여 접근권한을 부여하는 방식이다.
- 시스템이 접근통제 권한을 지정한다.
- 데이터베이스 객체별로 보안 등급을 부여할 수 있다.
- 사용자별로 인가 등급을 부여할 수 있다.

[   ]

- 사용자의 역할에 따라 접근 권한을 부여하는 방식이다
- 중앙관리자가 접근통제 권한을 지정한다.
- 임의 접근통제와 강제 접근 통제의 단점을 보완하였다.
- 다중 프로그램밍 환경에 최적화된 방식이다.

[   ]

- 데이터에 접근하는 사용자의 신원에 따라 접근 권한을 부여하는 방식이다.
- 데이터 소유자가 접근통제 권한을 지정하고 제어한다.
- 객체를 생성한 사용자가 생성된 객체에 대한 모든 권한을 부여받고, 부여된 권한을 다른 사용자에게 허가할 수도 있다.

> MAC RBAC DAC
> 

## 다음 셜명에 해당하는 프로토콜을 쓰시오

- 거리 벡터 라우팅 프로토콜이라고도 불리며, 최단 경로 탐색에 Bellman-Ford알고리즘이 사용된다.
- 소규모 동종의 네트워크 내에서는 효율적이나, 최대 홉 수가 제한되므로 대규모 네트어크에서는 사용할 수 없다.
- 일정 시간 동안 라우팅 정보가 갱신되지 않으면 해당 경로를 이상 상태로 간주한다.

> RIP
> 

## 관계 연산자에 대한 다음 설명에서 각 번호의 연산자를 의미하는 기호를 보기에 찾아 쓰시오

Join ⨝

Project π

Select σ

Division ÷

## 다음은 JAVA에서, implement 패키지에서 execution 패키지의 Sample  클래스를 호출하는 코드를 구현한 것이다. 괄호(ㄱ, ㄴ)에 들어갈 알맞은 코드를 쓰시오.

```python
(  ㄱ  ) implement;
(  ㄴ  ) exeution.Sample;

public class Test {
	public static void main (String[] args) {
		...
```

- ㄱ : Package
- ㄴ : import

## C언어의 헤더 파일 중 ‘sdlib.h’가 제공하는 기능에 대해 간략히 서술하시오

- sdlib.h : 자료형 변환, 난수 발생, 메모리 할당에 사용되는 기능을 제공합니다.

## Java에서 날짜 처리, 난수 발생, 복작한 무자열 처리 등에 관련되 기능을 제공하는 표준 라이브러리로 Date, Calender, Rondom, String Tokenizer 등의 다양한 클래스가 포함되어 있는 패키지의 이름을 쓰시오

- import unti

## 다음은 난수 알고리즘을 이용하여 6면 주사위를 100번 굴려서 나온 각 면의 수를 배열에 저장하여 출력하는 알고리즘을 Python으로 구현한 코드이다. 프로그램을 분석하여 괄호( 1 ~ 3 ) 에 들어갈 가장 적합한 코드를 쓰시오

```python
import random
hist = [ 0, 0, 0, 0, 0, 0]
for i in range(100);
	n = ( 1 ).randrange(1, 7)
	hist[( 2 )] += 1
i = 0
while i < 6:
	print("[%d] = %d" % (i + 1, ( 3 ) ))
	i += 1
```

> 1 : random
2 : n - 1
3 : hist[i]
> 

### n = (random).randrange(1, 7)

- random클래스의 메소드 randrange()를 수행하여 1 ~ 6사이의 정수 난수를 n에 저장한다.

### hist[(n-1)] += 1

- 주사위의 면은 1 ~ 6이고 hist의 위치는 0 ~ 5이기 때문에 n - 1을 위치에 저장한다.

## 선언형 프로그램밍 언어는 프로그램이 수행해야 할 문제를 기술하는 언어로, 목표를 명시하고 알고리즘은 명시하지 않는 특징이 있다. 다음에서 선언형 프로그램 언어를 모두 골라 쓰시오

HTML, LISP, FORTRAN, COBOL, XML, Haskell, C, java

> HTML, LISP, XML, Haskell
> 

## 수치 계산이나 논리 연산에 특화되어 있어 과학 기술 계산용으로 주로 사용되며, PASCAL과 C언어의 모체가 된 정차적 프로그래밍 언어는 무엇인지 쓰시오.

- ALGOL
