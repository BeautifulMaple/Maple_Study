# 구조체란

- 자료의 종류가 다른 변수의 모임

```c
struct sawon{
	char name[0];
	char jilwi[10];
	int pay;
};
```

> struct : 구조체를 정의하는 예약어
sawon : 구초체의 이름으로 사용자가 임의로 정할 수 있다.
멤버 : 일반 변수를 선언하는 것과 동일하게 필요한 필드을 임의로 선언한다.
> 

## 구조체 변수의 선언

구조체 변수를 사용하려면 먼저 정의한 구조체에 대한 변수를 선언해야 한다.

`strucr sawon ansan, *seoul;`

> `ansan`은 구조체 `sawon` 타입의 변수입니다.

`*seoul`은 구조체 `sawon` 타입의 포인터 변수입니다.
> 

## 구조체 멤버의 지정

구조체 변수를 사용하여 멤버에 접근하는 방법은 다음과 같습니다.

### 일반 변수의 경우

구조체 일반 변수를 이용해  구조체 멤버를 지정할 때 `.` (dot)연산자를 사용합니다.

```csharp
ansan.name = "홍길동";
ansan.jilwi = "과장";
ansan.pay = 5000;
```

### 포인터 변수의 경우

구조체 포인터 변수를 통해 멤버에 접근할 때는  `->` (arrow)연산자를 사용합니다.

```csharp
seoul->name = "홀길동";
seoul->jikwi = "과장";
seoul->pay = 5000;
```

구조체의 포인터 변수는 일반 포인터 변수처럼 `*`를 사용하여 멤버를 지정할 수도 있습니다.

```csharp
(*ansan).name = "홍길동";
(*seoul).jilwi = "과장";
(*ansan).pay = 5000;
```

### 구조체 초기화

구조체 변수를 초기화하는 방법은 다음과 같습니다.

```csharp
struct sawon ansan = {"홍길동", "과장", 5000};
```

## 예시 프로그램

```c
#include <string.h>

struct jsu {
	char nae[12];
	int os, db, hab, hhab;
};

int main(){
	struct jsu st[3] = {{"데이터1", 95, 88}, {"데이터2", 84, 91}, {"데이터3", 86, 75}};
	struct jsu *p ;
	p = &st[0];
	
	(p + 1)->hab = (p + 1)->os + (p + 2)->db;
	(p + 1)->hhab = (p + 1)->hab + p->os + p->db;
	printf("%d", (p + 1)->hab + (p + 1)->hhab);
}
```

구조체 배열을 선언하고 초기화를 하면

|  | char nae[12] |  |  |  |  | int os | int db | int hab | int hhab |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| st[0] | ‘데’ | ‘이’ | ‘터’ | 1 | ‘\0’ | 95 | 88 |  |  |
| st[1] | ‘데’ | ‘이’ | ‘터’ | 2 | ‘\0’ | 84 | 91 |  |  |
| st[2] | ‘데’ | ‘이’ | ‘터’ | 3 | ‘\0’ | 86 | 75 |  |  |
- 문자열을 저장하는 경우 문자열의 끝을 의미하는 널 문자(’\0’)가 추가로 저장됩니다.
- 출력 시 널 문자는 표시되지 않습니다.
- 영문, 숫자는 1byte, 한글은 2Byte를 차지한다.

### (p + 1)->hab = (p + 1)->os + (p + 2)->db;

- p + 1이 가리키는 hab에 p + 1이 가리키는 os, p + 2가 가리키는 db의 값을 더한 후 저장합니다.
- (P + 1)→hab = 84 + 75 = 159

|  | char nae[12] |  |  |  |  | int os | int db | int hab | int hhab |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| st[0] | ‘데’ | ‘이’ | ‘터’ | 1 | ‘\0’ | 95 | 88 |  |  |
| st[1] | ‘데’ | ‘이’ | ‘터’ | 2 | ‘\0’ | 84 | 91 | 159 | 342 |
| st[2] | ‘데’ | ‘이’ | ‘터’ | 3 | ‘\0’ | 86 | 75 |  |  |

## (p + 1)->hhab = (p + 1)->hab + p->os + p->db;

- p + 1이 가리키는 hhab에 p + 1가 가리키는 hab(159), p가 가리키는 os, db의 값을 더한 후 저장합니다.
- (p + 1)->hhab = 159 + 95 + 88 = 342

## printf("%d", (p + 1)->hab + (p + 1)->hhab);

- (p + 1)->hab + (p + 1)->hhab의 값을 더한 다음 출력합니다
- 159 + 342 = 501

### 중첩 구조체

구조체 내에 또 다른 구조체를 포함시킬 수 있습니다. 이를 통해 더 복잡한 데이터 구조를 만들 수 있습니다.

```c
struct address {
    char city[20];
    char street[20];
};

struct sawon {
    char name[10];
    char jilwi[10];
    int pay;
    struct address addr;
};
```

### 익명 구조체

익명 구조체는 구조체 이름을 생략하고 정의할 수 있으며, 주로 한 번만 사용될 구조체에 유용합니다.

```c
struct {
    char name[10];
    int age;
} person;
```

### 공용체와의 조합

구조체와 공용체를 함께 사용하여 메모리 효율성을 높일 수 있습니다.

```c
union Data {
    int i;
    float f;
    char str[20];
};

struct Example {
    int type;
    union Data data;
};
```
