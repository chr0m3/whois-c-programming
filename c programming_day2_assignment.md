# C Programming - Day 2

## 읽을거리

## 과제

### Day2-Q1

* 보고서에 작성하시오.

#### 문제

Automatic Variable, Global Variable, Extern Variable, Static Variable, Register Variable, Volatile Variable에 대해 설명하시오.

### Day2-Q2

* 보고서에 작성하시오.

#### 문제

Call by Reference와 Call by Value를 비교하시오.

### Day2-Q3

* 파일명 : day2_q3.c

#### 문제

두 실수를 인자로 받아 곱한 값을 반환하는 함수 `multiply()` 를 정의하고, 이를 이용한 곱셈 프로그램을 구현하시오.

#### 예제

##### 입력1

```text
3 8
```

##### 출력1

```text
24
```

##### 입력2

```text
5 4
```

##### 출력2

```text
20
```

### Day2-Q4

* 파일명 : day2_q4.c

#### 문제

정수 n을 인자로 받아 피보나치 수열의 n번째 항을 반환하는 함수 `fibonacci()`를 재귀적으로 구현하시오. 피보나치 수열은 점화식 ![eq](https://latex.codecogs.com/png.latex?%5Cinline%20%5Cdpi%7B100%7D%20a_%7Bn&plus;2%7D%20%3D%20a_%7Bn&plus;1%7D%20&plus;%20a_%7Bn%7D%20%28n%20%5Cin%20%5Cmathbb%7BN%7D%2C%20a_%7B1%7D%20%3D%20a_%7B2%7D%20%3D%201%29) 을 만족하는 수열로 `1, 1, 2, 3, 5, 8, ...` 이다.

#### 예제

##### 입력1

```text
5
```

##### 출력1

```text
5
```

##### 입력2

```text
8
```

##### 출력2

```text
21
```

### Day2-Q5

* 파일명 : day2_q5.c

#### 문제

배열에 문자열을 입력받아 그대로 출력하는 프로그램을 구현하시오.

#### 예제

##### 입력1

```text
hello, world!
```

##### 출력1

```text
hello, world!
```

##### 입력2

```text
array
```

##### 출력2

```text
array
```

### Day2-Q6

* 파일명 : day2_q6.c

#### 문제

길이가 같은 두 개의 배열을 선언하시오. 한 배열에 문자열을 입력받아 저장하고, 두 배열에 저장된 값을 각각 출력하는 프로그램을 만드시오.

#### 예제

##### 입력1

```text
hello, world!
```

##### 출력1

```text
array 1 : hello, world!
array 2 : hello, world!
```

##### 입력2

```text
array
```

##### 출력2

```text
array 1 : array
array 2 : array
```

### Day2-Q7

* 파일명 : day2_q7.c

#### 문제

길이가 10인 정수형 배열을 선언하시오. 이 배열에 10개의 정수를 입력받은 후, 오름차순(작은 수부터 큰 수로)으로 정렬하여 출력하는 프로그램을 구현하시오.

#### 예제

##### 입력1

```text
2 6 3 8 1 9 0 4 5 7
```

##### 출력1

```text
0 1 2 3 4 5 6 7 8 9
```

### Day2_Q8

* 파일명 : day2_q8.c

#### 문제

길이가 100인 정수형 배열을 선언하시오. 이 배열에 50개의 정수를 입력받은 후, 입력값을 오름차순으로 정렬하고, 원하는 숫자가 몇 번째에 있는지 이진탐색으로 찾아 몇 번째 index에 있는지 출력하는 프로그램을 구현하시오.

#### 예제

예제에서는 10개의 정수를 입력한 상황을 가정하였음.

##### 입력1

```text
2 6 3 8 1 9 0 4 5 7
3
```

##### 출력1

```text
allign
0 1 2 3 4 5 6 7 8 9
3
```

##### 입력2

```text
25 61 32 82 13 93 4 48 53 77
77
```

##### 출력2

```text
allign
4 13 25 32 48 53 61 77 82 93
7
```

### Day2_Q9

* 파일명 : day2_q9.c

#### 문제

크기가 2*2인 `double`형의 2차원 배열을 선언하시오. 행과 열이 각각 2개인 이차정사각행렬을 입력받아 역행렬을 구하는 프로그램을 구현하시오. 단, 행렬식(Determinant)이 0일 경우 역행렬이 존재하지 않는다고 출력하시오.이차정사각행렬 ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cdpi%7B100%7D%20A%20%3D%20%5Cbegin%7Bpmatrix%7Da%20%26%20b%20%5C%5C%20c%20%26%20d%5Cend%7Bpmatrix%7D)의 역행렬 ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cdpi%7B100%7D%20A%5E%7B-1%7D)은 ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cdpi%7B100%7D%20%5Cfrac%7B1%7D%7BDet%28A%29%7D%5Cbegin%7Bpmatrix%7Dd%20%26%20-b%20%5C%5C%20-c%20%26%20a%5Cend%7Bpmatrix%7D)이고, 행렬식 ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cdpi%7B100%7D%20Det%28A%29)은 ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cdpi%7B100%7D%20ad%20-%20bc)이다.
#### 예제

##### 입력1

```text
1 2
1 3
```

##### 출력1

```text
3 -2
-1 1
```

### Day2_Q10

* 파일명 : day2_q10.c

#### 문제

변수 a와 b를 선언하고 각각 값을 입력받으시오. 두 변수에 저장된 값을 서로 바꿔주는 함수를 구현하시오.

#### 예제

##### 입력1

```text
2 7
```

##### 출력1

```text
before
a : 2
b : 7
after
a : 7
b : 2
```

##### 입력2

```text
23 86
```

##### 출력2

```text
before
a : 23
b : 86
after
a : 86
b : 23
```