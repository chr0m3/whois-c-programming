# C Programming - Day 3

## 읽을거리

## 과제

### Day3-Q1

* 보고서에 작성하시오.

#### 문제

포인터가 반드시 필요한 상황 하나를 제시하고, 왜 포인터가 필요한지 설명하시오.

### Day3-Q2

#### 문제

포인터에 대해 아는 대로 모두 설명하시오.

### Day3-Q3

* 파일명 : day3_q3.c

#### 문제

길이가 5인 배열 `arr`을 선언하고, `{1, 3, 5, 7, 9}`로 초기화하시오. 이 배열과 정수 값 하나를 인자로 전달받아 배열의 모든 원소에 정수 값을 더하는 함수 `add_int()`를 구현하시오. 정수 값을 더한 결과도 출력하시오.

#### 예제

##### 입력 1

```text
5
```

##### 출력 1

```text
6, 8, 10, 12, 14
```

### Day3-Q4

* 파일명 : day3_q4.c

#### 문제

크기가 32Byte인 char형 배열 `stack`을 선언하고, 스택의 맨 위를 가리키는 스택 포인터 변수 `sp`를 선언하시오. 이를 이용해 아래와 같은 기능을 갖는 스택을 구현하시오.

1. push : 스택의 맨 위에 값 추가한다.
2. pop : 스택의 맨 위에 있는 값을 출력하고 삭제한다.
3. show : 현재 스택에 저장된 모든 데이터와 현재 스택 포인터가 가리키는 위치를 출력한다.
4. quit : 프로그램을 종료한다.

#### 예제

* 예제는 스택의 크기를 8Byte로 가정함.

```text
[Menu]
1. push
2. pop
3. show
4. quit

Menu : 
```

초기화된 배열의 상태는 다음과 같을 것이고, 스택에 아무 데이터도 없으므로 `sp`의 값은 `0x107`일 것이다.

```text
[stack]
index		addr	value
stack[0]	0x100	0
stack[1]	0x101	0
stack[2]	0x102	0
stack[3]	0x103	0
stack[4]	0x104	0
stack[5]	0x105	0
stack[6]	0x106	0
stack[7]	0x107	0		<- sp
```

스택에 값을 push하면 현재 `sp`가 가리키는 곳에 데이터를 저장하고, `sp`를 1 감소시킨다. 만약 값 3개(10, 20, 30)를 push하면 `stack`은 다음과 같이 변화할 것이고, `sp`의 값은 `0x104`가 될 것이다. 

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
[stack]
index		addr	value
stack[0]	0x100	0
stack[1]	0x101	0
stack[2]	0x102	0
stack[3]	0x103	0
stack[4]	0x104	0		<- sp
stack[5]	0x105	30
stack[6]	0x106	20
stack[7]	0x107	10
```

스택의 값을 pop하면 현재 `sp`가 가리키는 곳 바로 다음 데이터를 출력하고, `sp`를 1 증가시킨다.

```text
Menu : 2

Pop 30

Menu : 
```

```text
[stack]
index		addr	value
stack[0]	0x100	0
stack[1]	0x101	0
stack[2]	0x102	0
stack[3]	0x103	0
stack[4]	0x104	0
stack[5]	0x105	30		<- sp
stack[6]	0x106	20
stack[7]	0x107	10
```

```text
Menu : 2

Pop 20

Menu : 
```

```text
[stack]
index		addr	value
stack[0]	0x100	0
stack[1]	0x101	0
stack[2]	0x102	0
stack[3]	0x103	0
stack[4]	0x104	0
stack[5]	0x105	30
stack[6]	0x106	20		<- sp
stack[7]	0x107	10
```

이 상태에서 show하면 다음과 같이 출력한다.

```text
Menu : 3

[Stack]
addr	value
0x100	0
0x101	0
0x102	0
0x103	0
0x104	0
0x105	30
0x106	20		<- sp
0x107	10
```

여기에서 다시 push를 하면 데이터가 덮어씌워질 것이다.

```text
Menu : 1

Value : 40
Insert 40

Menu : 
```

```text
[stack]
index		addr	value
stack[0]	0x100	0
stack[1]	0x101	0
stack[2]	0x102	0
stack[3]	0x103	0
stack[4]	0x104	0
stack[5]	0x105	30		<- sp
stack[6]	0x106	40
stack[7]	0x107	10
```

```text
Menu : 4

Exit
```

### Day3-Q5

* 파일명 : day3_q5.c

#### 문제

길이가 50인 정수형 배열과 `num_arr`와, 이 배열의 원소를 가리키는 포인터 배열 `ptr_arr`를 선언하시오. `num_arr`에 50개의 정수를 입력받으시오. `ptr_arr`의 원소를 바꿔(`ptr_arr`의 원소가 가리키는 `num_arr`의 원소를 바꿔) 입력된 정수들을 오름차순(작은 수부터 큰 수)으로 정렬하는 함수 `sort_arr()`와 정렬된 결과를 출력하는 함수`show_arr()`를 정의하여 정렬된 결과를 출력하시오.

#### 예제

* 예제는 배열과 입력값의 길이를 모두 10으로 가정함

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

`ptr_arr`의 원소들이 가리키는 값이 오름차순이 되도록 `ptr_arr`의 원소들의 순서를 바꾸면 다음과 같이 바뀔 것이다.

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

### Day3-Q6

* 파일명 : day3_q6.c

Day2-Q11의 코드에 아래와 같은 기능을 하는 함수를 정의해 기능을 추가하시오.

1. 성적 검색
2. 성적 수정