# C언어의 포인터

- 변수의 주소
- 데이터가 저장된 메모리의 시작 주소
    - 주소값을 1바이트 크기의 메모리 공간으로 나누어 표현합니다.
    - 예를 들어, int형 데이터는 4바이트의 크기를 가지지만, int형 데이터의 주소값은 시작 주소 1바이트만을 가리킵니다.
    

    
![Untitled](https://github.com/BeautifulMaple/Maple_Study/assets/114921436/5265cc57-6f6b-4a3f-8103-56f207bae5b7)

```c
int n = 100; // 변수의 선언
int *ptr = &n; // 포인터의 선
```

## 포인터 연산자

1. 주소 연산자(&)
    1. 변수의 이름 앞에 사용하여 해당 주소값을 반환합니다.
    2. ‘&’ 기호는 앰퍼샌드(ampersand)라고 읽으며, 번지 연산자라고도 불립니다.
2. 참조 연산자(*)
    1. 포인터의 이름이나 주소 앞에 사용하여, 포인터에 가리키는 주소에 저장된 값을 반환합니다.

![Untitled3](https://github.com/BeautifulMaple/Maple_Study/assets/114921436/7e3393b6-de24-42db-bb73-24990013be12)
![Untitled2](https://github.com/BeautifulMaple/Maple_Study/assets/114921436/fe556718-4d97-4496-a2e9-05659d6f31b1)


```c
#include <stdio.h>
main() {
	int a = 50;
	int *b = &a;
	int *b = *b + 20;
	printf("%d, %d\n", a, *b);
	
	char *s;
	s = "test";
	for (int i = 0; i < 4; i +=2)
	{
		printf("%c, " s[i]);
		printf("%c, " *(s + i));
		printf("%s\n", s + i); 
	}
	----------
	70, 70
	t, t, test
	s, s, st
```

int *b = &a;

- 정수형 변수가 저장된 곳의 주소를 기억할 포인트 변수 b를 선언하고,
- a의 주소로 초기화한다. b에는 a의 주소가 저장된다.

int *b = *b + 20;

- b가 가리키는 곳의 값(*b)에 20을 더한다. b가 가리키는 곳이 a이므로 결국 a의 값도 바뀌는 것이다.
- b가 가리키는 곳의 값에 20을 더해 다시 b가 가리키는 곳에 저장한다.
- 그곳은 변수 a의 주소이므로 변수 a의 값도 저절로 변경되는 것이다.

s = test

| 주소 | 1Byte | 1Byte | 1Byte | 1Byte |
| --- | --- | --- | --- | --- |
| 1000 | ‘t’ | ‘e’ | ‘s’ | ‘t’ |
|  | s
&s[0]
1000 + 0 | s + 1 
&s[1]
1000 + 1 | s + 2 
&s[2]
1000 + 2 | s + 3 
&s[3]
1000 + 3 |

printf("%c, " s[i]);

- i = 0 부터 i += 2 만큼 증가한다.
- s[0] = t가 있기 때문에
    - 출력 : t,

printf("%c, " *(s + i));

- (s+i) ⇒ ( s + 0)이 가리키는 곳의 문자로 출력한 후 ‘,’와 공백을 남긴다.
    - 출력 : t, t,

printf("%s\n", s + i);

- (s+i) ⇒ ( s + 0)의 위치부터 문자열의 끝 (’\0’)까지의 모든 문자를 하나의 문자열로 출력하고 커서를 다음 줄의 처음으로 옮긴다.
    - 출력 : t, t, test
---

- 문제 1
    
    ```c
    #include <stdio.h>
    
    int main() {
    	char *p = "KOREA";
    	printf("%s\n", p); // p의 위치에서 '\0'까지 출력 : KOREA
    	printf("%s\n", p + 3); // p + 3의 위치부터 '\0'까지 출력 : EA
    	printf("%s\n", *p); //p가 가리키고 있는 곳의 문자를 출력 : K
    	printf("%s\n", *(p + 3)); //p + 3이 가리키는 곳의 값을 문자로 출력 : E
    	printf("%s\n", *p + 2); // p가 가리키는 값에 + 2 한 값을 출력 : (*p = p[0] = K) + 2 => M
    }
    ```
    
    > KOREA
    EA
    K
    E
    M
    > 
- 문제 2
    
    ```c
    #include <stdio.h>
    
    int main() {
    	int ary[3]:
    	int s = 0;
    	*(ary + 0) = 1; // *ary = &ary[0] = ary[0] = 1
    	ary[1] = *(ary + 0) + 2; //ary[1] = ary[0] + 2 = 1 + 2 = 3
    	ary[2] = *ary + 3; //ary[2] = 1 + 3 = 4
    	for(int i = 0; i < 3; i++)
    		s = s + ary[i]; // s = (s + ary[0]) -> (s + ary[1]) -> (s + ary[2])
    	printf("%d", s); // 8
    }
    ```
    
    > 8
    > 
- 문제 3
    
    ```c
    #include <stdio.h>
    
    int main() {
    	int *array[3]:
    	int a = 12, b = 24, c = 36;
    	array[0] = &a; //array[0] = &a = a = 12
    	array[1] = &b; //array[1] = &b = b = 24
    	array[2] = &c; //array[2] = &c = c = 36
    	printf("%d", *array[1] + **array + 1);
    	// *array[1] = 24
    	// **array = *array = array[0] = 12
    	// 24 + 12 + 1 = 37
    }
    ```
    
    > 37
    >
