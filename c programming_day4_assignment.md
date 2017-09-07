# C Programming - Day 4

## 읽을거리

## 과제

### Day4-Q1

* 파일명 : day4_q1.c

#### 문제

크기가 32Byte인 char형 배열 `queue`를 선언하고, 큐의 맨 앞을 가리키는 포인터 `first`와 큐의 맨 뒤를 가리키는 포인터 `last`를 선언하시오. 이들을 이용하여 큐를 구현하시오.

1. enqueue : 큐의 맨 뒤에 값을 추가한다.
2. dequeue : 스택의 맨 앞에 있는 값을 출력하고 삭제한다.
3. show : 현재 큐에 저장된 모든 데이터와 포인터들을 출력한다.
4. quit : 프로그램을 종료한다.

##### 기타 조건
* 오류가 발생할 수 있는 상황을 모두 찾아 적절히 예외처리하시오.

#### 예제

* 예제는 배열의 크기를 8Byte로 가정함.

```text
[Menu]
1. enqueue
2. dequeue
3. show
4. quit

Menu :
```

초기화된 배열의 상태는 다음과 같을 것이고, 큐에 아무 데이터도 없으므로 `first`의 값은 `0x100`, `last`의 값은 `0x101`일 것이다.

```text
[queue]
index		addr	value
queue[0]	0x100	0       <- first
queue[1]	0x101	0       <- last
queue[2]	0x102	0
queue[3]	0x103	0
queue[4]	0x104	0
queue[5]	0x105	0
queue[6]	0x106	0
queue[7]	0x107	0
```

큐에 값을 enqueue하면 현재 `last`가 가리키는 곳에 데이터를 저장하고, `last`를 1 증가시킨다. 만약 값 3개(10, 20, 30)를 push하면 `queue`는 다음과 같이 변화할 것이고, `last`의 값은 `0x104`가 될 것이다.

```text
Menu : 1

Value : 10
Insert 10

Menu : 1

Value : 20
Insert 20

Menu : 1

Value : 30
Insert 30

Menu :
```

```text
[queue]
index		addr	value
queue[0]	0x100	0       <- first
queue[1]	0x101	10
queue[2]	0x102	20
queue[3]	0x103	30
queue[4]	0x104	0		<- last
queue[5]	0x105	0
queue[6]	0x106	0
queue[7]	0x107	0
```

큐에서 값을 dequeue하면 현재 `first`가 가리키는 곳 바로 다음 데이터를 출력한 뒤 0으로 초기화하고, `first`를 1 증가시킨다.

```text
Menu : 2

Pop 10

Menu :
```

```text
[queue]
index		addr	value
queue[0]	0x100	0
queue[1]	0x101	0       <- first
queue[2]	0x102	20
queue[3]	0x103	30
queue[4]	0x104	0       <- last
queue[5]	0x105	0
queue[6]	0x106	0
queue[7]	0x107	0
```

```text
Menu : 2

Pop 20

Menu :
```

```text
[queue]
index		addr	value
queue[0]	0x100	0
queue[1]	0x101	0
queue[2]	0x102	0       <- first
queue[3]	0x103	30
queue[4]	0x104	0       <- last
queue[5]	0x105	0
queue[6]	0x106	0
queue[7]	0x107	0
```

이 상태에서 show하면 다음과 같이 출력한다.

```text
Menu : 3

[queue]
addr	value
0x100	0
0x101	0
0x102	0       <- first
0x103	30
0x104	0       <- last
0x105	0
0x106	0
0x107	0
```

여기에서 다시 push를 하면 데이터가 이어붙여질 것이다.

```text
Menu : 1

Value : 40
Insert 40

Menu :
```

```text
[queue]
index		addr	value
queue[0]	0x100	0
queue[1]	0x101	0
queue[2]	0x102	0       <- first
queue[3]	0x103	30
queue[4]	0x104	40
queue[5]	0x105	0		<- last
queue[6]	0x106	0
queue[7]	0x107	0
```

```text
Menu : 4

Exit
```

### Day4-Q2

* 파일명 : day4_q2.c

#### 문제

Brainfuck 언어는 아래의 8개의 명령어만을 가지는 튜링 완전한 언어이다. Brainfuck 언어로 작성된 프로그램을 입력받아 실행하는 인터프리터를 구현하시오. 

##### 기타 조건
* 길이가 10240인 `char`형 배열을 선언하여 프로그램을 입력받으시오.
* 길이가 1024인 `char`형 배열을 선언하여 메모리로 사용하시오.
* 포인터 변수 `ptr`을 선언하여 메모리를 가리키는 포인터로 사용하시오.
* 프로그램은 줄바꿈 또는 띄어쓰기 없이 한 줄로 입력된다.
* `[`와 `]` 명령어는 중첩되지 않고 사용된다.
* 오류가 발생할 수 있는 상황을 모두 찾아 적절히 예외처리하시오.

##### Brainfuck 명령어
`>` : 포인터를 1 증가시킨다.
`<` : 포인터를 1 감소시킨다.
`+` : 포인터가 가리키는 바이트의 값을 증가시킨다.
`-` : 포인터가 가리키는 바이트의 값을 감소시킨다.
`.` : 포인터가 가리키는 바이트에 저장된 값을 아스키 문자로 출력한다. 예를 들어 `0x41`이 저장되어 있다면 `A`를 출력한다.
`,` : 사용자로부터 입력을 받아 포인터가 가리키는 바이트에 입력한 문자의 아스키 코드 값을 저장한다. 예를 들어 `A`를 입력하면 `0x41`을 저장한다.
`[` : 포인터가 가리키는 바이트의 값이 0이면 `]`가 있는 곳으로 건너뛴다.
`]` : 포인터가 가리키는 바이트의 값이 0이 아니면 `[`가 있는 곳으로 건너뛴다.

#### 예제

##### 입력1

```text
++++++++++[>+++++++>++++++++++>+++>+<<<<-]>++.>+.+++++++..+++.>++.<<+++++++++++++++.>.+++.------.--------.>+.>.
```

##### 출력1

```text
Hello, World!
```

### Day4-Q3

* 파일명 : day4_q3.c

#### 문제

길이가 50인 배열 `arr[50]`와 포인터 배열 `ptr_arr[50]` 하나를 선언하시오. 정수 50개를 입력받아 `arr`에 저장하시오. `ptr_arr`는 배열의 원소를 순서대로 가리키도록 초기화하시오. 예를 들어 `ptr_arr[0]`은 `arr[0]`을 가리켜야 하고, `ptr_arr[10]`은 `arr[10]`을 가리켜야 한다. `ptr_arr[0]`가 가리키는 변수를 바꿔 작은 수부터 큰 수까지 가리키도록 정렬하고 출력하는 프로그램을 구현하시오.

##### 기타 조건
* 포인터 배열을 인자로 전달받아 정렬하는 함수를 정의하여 구현하시오.
* 전역 변수를 사용하지 마시오.
* 오류가 발생할 수 있는 상황을 모두 찾아 적절히 예외처리하시오.

#### 예제

* 예제는 배열과 입력값의 길이를 모두 10으로 가정한다.

입력값이 아래와 같다고 가정하자.

```text
78 26 34 87 16 53 93 47 62 102
```

`num_arr`가 `0x100~0x127`까지 할당되었다고 가정하면, 이 정수들은 메모리에 다음과 같이 저장될 것이다.

```text
[num_arr]
index		addr	value
num_arr[0]	0x100	78
num_arr[1]	0x104	26
num_arr[2]	0x108	34
num_arr[3]	0x10c	87
num_arr[4]	0x110	16
num_arr[5]	0x114	53
num_arr[6]	0x118	93
num_arr[7]	0x11c	47
num_arr[8]	0x120	62
num_arr[9]	0x124	102
```

그리고 배열 `num_arr`의 원소들을 가리키는 포인터들의 배열 `ptr_arr`는 다음과 같이 초기화될 것이다.

```text
[ptr_arr]
index		value	reference	ref_value
ptr_arr[0]	0x100	num_arr[0]	78
ptr_arr[1]	0x104	num_arr[1]	26
ptr_arr[2]	0x108	num_arr[2]	34
ptr_arr[3]	0x10c	num_arr[3]	87
ptr_arr[4]	0x110	num_arr[4]	16
ptr_arr[5]	0x114	num_arr[5]	53
ptr_arr[6]	0x118	num_arr[6]	93
ptr_arr[7]	0x11c	num_arr[7]	47
ptr_arr[8]	0x120	num_arr[8]	62
ptr_arr[9]	0x124	num_arr[9]	102
```

`ptr_arr`의 원소들이 가리키는 값이 오름차순이 되도록 `ptr_arr`의 원소들의 순서를 바꾸어 정렬하면 다음과 같이 바뀔 것이다.

```text
[ptr_arr(after sort)]
index		value	reference	ref_value
ptr_arr[0]	0x110	num_arr[4]	16
ptr_arr[1]	0x104	num_arr[1]	26
ptr_arr[2]	0x108	num_arr[2]	34
ptr_arr[3]	0x11c	num_arr[7]	47
ptr_arr[4]	0x114	num_arr[5]	53
ptr_arr[5]	0x120	num_arr[8]	62
ptr_arr[6]	0x100	num_arr[0]	78
ptr_arr[7]	0x10c	num_arr[3]	87
ptr_arr[8]	0x118	num_arr[6]	93
ptr_arr[9]	0x124	num_arr[9]	102
```

이제 정렬된 `ptr_arr`를 이용해 입력된 정수를 오름차순으로 출력하면 아래와 같은 결과를 얻을 수 있다.

```text
16 26 34 47 53 62 78 87 93 102
```

#### 조건

* 전역변수를 사용하지 마시오.
* `ptr_arr`를 정렬하는 함수 `sort_arr()`를 정의하시오.
* 정렬된 결과를 출력하는 함수 `print_arr()`를 정의하시오.
* 조건을 지키지 않는 경우 감점 또는 오답처리함.
* 오류가 발생할 수 있는 상황을 모두 찾아 적절히 예외처리하시오.

### Day4-Q4

* 파일명 : day4_q4.c

#### 문제

day3_q11 문제 성적관리프로그램을 수정하시오.

1. 소학회원의 정보를 구조체 배열을 이용하여 저장하도록 하시오. 구조체의 구조는 다음과 같다.

```c
struct Score {
    float score1;  // 성적1
    float score2;  // 성적2
    float score3;  // 성적3
    float score4;  // 성적4
    float score5;  // 성적5
};

struct Member {
	int student_no;  // 학번
    char name[10];  // 이름
    Score score;  // 성적 구조체
};
```

2. 소학회원의 학번을 입력하면 해당 소학회원의 정보를 출력하도록 검색 기능을 추가하시오.

```text
[메인 메뉴]

1. 전체 소학회원 정보 출력
2. 소학회원 등록
3. 소학회원 정보 검색
0. 프로그램 종료

메뉴: 3

검색할 학번 : 201712345

결과를 찾았습니다.
학번 : 201712345
이름 : 후이즈
성적1 : 3.5
성적2 : 3.6
성적3 : 3.7
성적4 : 3.8
성적5 : 3.9
평균성적 : 3.7
```

3. 성적 순서대로 정렬하여 출력하는 기능은 학번 오름차순(작은 번호부터 큰 번호)으로 정렬하여 출력하도록 하시오.

```text
[메인 메뉴]

1. 전체 소학회원 정보 출력
2. 소학회원 등록
3. 소학회원 정보 검색
0. 프로그램 종료

메뉴: 1

[전체 소학회원 정보 출력]
1. 등록 순서대로 출력
2. 학번 순서대로 출력
0. 메인으로 돌아가기

메뉴 : 2

[전체 소학회원 정보]
학번 : 201712345
이름 : 후이즈
성적 : 3.7

학번 : 201723456
이름 : 곽진
성적 : 3.8
```