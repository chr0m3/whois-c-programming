# C Programming - Day 5

## 읽을거리

* [C standard library](https://en.wikipedia.org/wiki/C_standard_library)

## 과제

### Day5-Q1

* 파일명 : day5_q1.c

#### 문제

정수 값을 저장할 수 있는 Stack을 Linked List를 이용하여 구현하시오. 이 프로그램은 다음과 같은 기능을 가진다.

1. push : 맨 위에 새로운 값을 추가
2. pop : 맨 위의 값을 출력한 후 제거
3. show : 스택에 저장된 모든 값을 먼저 push한 순서대로 출력

##### 기타 조건

* 오류가 발생할 수 있는 상황을 모두 찾아 적절히 예외처리하시오.
* 구조체를 이용하시오.

#### 예제

프로그램을 실행하면 아래와 같은 메뉴를 보여준다.

```text
[Stack]
1. push
2. pop
3. show
0. quit

Menu :
```

사용자가 세 개의 값 10, 20, 30을 push한 후 show를 선택하면 다음과 같이 보여준다.

```text
Menu : 1

[Push]
Value : 10

Pushed 10

Menu :
```

```text
Menu : 1

[Push]
Value : 20

Pushed 20

Menu :
```

```text
Menu : 1

[Push]
Value : 30

Pushed 30

Menu :
```

```text
Menu : 3

[Show All]
1 : 10
2 : 20
3 : 30

Menu :
```

이 상태에서 두 번 pop 한 후 다시 show를 하면 다음과 같다.

```text
Menu : 2

[Pop]
pop 30

Menu :
```

```text
Menu : 2

[Pop]
pop 20

Menu :
```

```text
Menu : 3

[Show All]
1 : 10

Menu :
```

### Day5-Q2

* 파일명 : day5_q2.c

#### 문제

정수 값을 저장할 수 있는 Queue를 Linked List를 이용하여 구현하시오. 이 프로그램은 다음과 같은 기능을 가진다.

1. enqueue : 맨 끝에 새로운 값을 추가
2. dequeue : 맨 앞의 값을 출력한 후 제거
3. show : 스택에 저장된 모든 값을 먼저 enqueue한 순서대로 출력

##### 기타 조건

* 오류가 발생할 수 있는 상황을 모두 찾아 적절히 예외처리하시오.
* 구조체를 이용하시오.

#### 예제

프로그램을 실행하면 아래와 같은 메뉴를 보여준다.

```text
[Queue]
1. enqueue
2. dequeue
3. show
0. quit

Menu :
```

사용자가 세 개의 값 10, 20, 30을 enqueue한 후 show를 선택하면 다음과 같이 보여준다.

```text
Menu : 1

[Enqueue]
Value : 10

Enqueued 10

Menu :
```

```text
Menu : 1

[Enqueue]
Value : 20

Enqueued 20

Menu :
```

```text
Menu : 1

[Enqueue]
Value : 30

Enqueued 30

Menu :
```

```text
Menu : 3

[Show All]
1 : 10
2 : 20
3 : 30

Menu :
```

이 상태에서 두 번 dequeue 한 후 다시 show를 하면 다음과 같다.

```text
Menu : 2

[Dequeue]
dequeue 10

Menu :
```

```text
Menu : 2

[Dequeue]
dequeue 20

Menu :
```

```text
Menu : 3

[Show All]
1 : 30

Menu :
```