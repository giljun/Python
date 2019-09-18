# Module

# 1 모듈 활용 기초

* python에는 기본적으로 제공되는 모듈들이 있음
* 표준 라이브러리](https://docs.python.org/ko/3/library/index.html)에서 제공되는 모듈을 확인 가능

## 1. `import`

* 모듈을 활용하기 위해서는 반드시 `import`를 통해 내장 모듈을 이름 공간으로 가져와야 함
* `import`는 다양한 방법으로 할 수 있음

```python
import random
lotto = random.sample(range(1, 46), 6)
print(lotto)
```



## 2. `from` 모듈명 `import` 어트리뷰트

* 특정한 함수 혹은 어트리뷰트만 활용하고 싶을 때 사용

```python
from random import sample
sample(range(1, 46), 6)
```



## 3. `from` 모듈명 `import` `*`

* 해당하는 모듈 내의 모든 변수, 함수, 클래스를 가져옴

```python
from random import *
# random에 있는 모든 것들 가져오기
choice(['소불고기', '날치알밥', '잔치국수'])
```



## 4. `from` 모듈명 `import` 어트리뷰트 `as`

* 내가 지정하는 이름을 붙여서 사용 가능
* 축약형으로 내가 지정할 수 있음
* 하지만 다른 사람들은 알아보기 힘드므로 사용하지 않는 것을 권장함

```python
from random import choice as c
c([1, 2])
```



# 2 숫자 관련 함수

* 이외에도 분수(fractions), 십진(decimal), 통계(statistics) 등이 있음

## 1. 수학 관련 함수(math)

* 기본 함수는 `import`없이 사용 가능
* 기본 함수 - `sum`, `max`, `min`, `abs`, `pow`, `round`, `divmod`
* `import`하면 활용할 수 있는 상수 - `pi`, `e`
* 활용할 수 있는 연산 관련 함수

| 함수                | 비고                            |
| ------------------- | ------------------------------- |
| math.ceil(x)        | 소수점 올림                     |
| math.floor(x)       | 소수점 내림                     |
| math.trunc(x)       | 소수점 버림                     |
| math.copysign(x, y) | y의 부호를 x에 적용한 값        |
| math.fabs(x)        | float 절대값 - 복소수 오류 발생 |
| math.factorial(x)   | 팩토리얼 계산 값                |
| math.fmod(x, y)     | float 나머지 계산               |
| math.fsum(iterable) | float 합                        |
| math.modf(x)        | 소수부 정수부 분리              |

* 로그, 지수 연산

| 함수                | 비고                  |
| ------------------- | --------------------- |
| math.pow(x,y)       | x의 y승 결과          |
| math.sqrt(x)        | x의 제곱근의 결과     |
| math.exp(x)         | e^x 결과              |
| math.log(x[, base]) | 밑을 base로 하는 logx |

* 삼각함수

| sin 함수| cos 함수 | tan 함수 |
| -------- | -------- | -------- |
| sin | cos | tan |
| asin | acos | atan |
| sinh | cosh | tanh |
| asinh | acosh | atanh |



## 2. 난수 발생관련 함수(random)

* `sample` : 임의의 값을 중복 없이 리스트로 반환
* `choice` : 임의의 값을 반환. 중복 가능성 있음
* `random` : 0.0 이상 1.0 미만의 실수(float)를 반환
* `randint` : 범위 내의 숫자 중 범위 마지막 숫자가 포함 된 정수(int)를 반환
* `seed` : 시드를 설정하지 않으면 현재 시간을 기반으로 임의의 숫자반환
* `shuffle` : 시퀀스 객체를 섞어서 반환



# 3 날짜 관련 모듈

## 1. datetime

* 날짜와 시간 관련 모듈
* 시간의 형식을 지정해서 반환할 수 있음

| 형식 지시자(directive) | 의미                   |
| ---------------------- | ---------------------- |
| %y                     | 연도표기(00~99)        |
| %Y                     | 연도표기(전체)         |
| %b                     | 월 이름(축약)          |
| %B                     | 월 이름(전체)          |
| %m                     | 월 숫자(01~12)         |
| %d                     | 일(01~31)              |
| %H                     | 24시간 기준(00~23)     |
| %I                     | 12시간 기준(01~12)     |
| %M                     | 분(00~59)              |
| %S                     | 초(00~61)              |
| %p                     | 오전/오후              |
| %a                     | 요일(축약)             |
| %A                     | 요일(전체)             |
| %w                     | 요일(숫자 : 일요일(0)) |
| %j                     | 1월 1일부터 누적 날짜  |

* datetime 의 메소드

| 속성/메소드 | 내용                 |
| ----------- | -------------------- |
| .year       | 년                   |
| .month      | 월                   |
| .day        | 일                   |
| .hour       | 시                   |
| .minute     | 분                   |
| .second     | 초                   |
| .weekday()  | 월요일을 0부터 6까지 |

* 특정한 날짜 만들기

>  datetime.date(year, month, day, hour, minute, second, microsecond)



## 2. timedelta

* from datetime import timedelta

* 비교 및 연산 가능

  