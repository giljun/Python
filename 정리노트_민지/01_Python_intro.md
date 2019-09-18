# Python_intro

# 1) Python 기초

## 1. 식별자

* python에서변수, 함수, 모듈, 클래스 등을 식별하는데 사용되는 이름

> 식별자의 이름은 영문 알파벳, _, 숫자로 구성
>
> 첫 글자에 숫자는 올 수 없음
>
> 대문자와 소문자를 구별함
>
> 아래의 예약어는 사용할 수 없음

```
False, None, True, and, as, assert, break, class, continue, def, del, elif, else, except, finally, for, from, global, if, import, in, is, lambda, nonlocal, not, or, pass, raise, return, try, while, with, yield
```

#### 식별자 확인하기

```python 
import keyword
print(keyword.kwlist)
```

``` python
# 결과
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

* 내장함수나 모듈 등의 이름으로도 만들면 안됨

```python
str(5)
>>> '5'
str = 'hello, world'
str(5)
>>> TypeError
```

* 이렇게 변수를 설정하면 뒤에서 나오는 코드에 영향이 갈 수 있으므로 변수를 메모리에서 지워줘야 함.

```python
del str
```



## 2. 기초 문법

### 인코딩 선언

> 인코딩은 선언하지 않아도 `UTF-8`로 기본 설정 되어있음.
>
> 만약, 인코딩을 설정하려면 코드 상단에 아래와 같이 선언해야 함. 주석으로 보이지만 Python `parser`에 의해 읽혀짐
>
> ```python
> # -*- coding: <encoding-name> -*- 
> ```



### 주석(Comment)

* 주석은 `#`으로 표현

* `docstring`은 `"""`으로 표현

  > docstring : 여러 줄의 주석을 작성할 수 있으며, 보통 함수/ 클래스 선언 다음에 해당하는 설명을 위해 활용

```python 
# 주석 연습
def mysum(a,b):    
    """
    이 함수는 더하기입니다.
    a와 b를 더한 결과를 출력합니다.
    docstring이라고 부릅니다.
    """
    print(a+b)
```

```python
# docstring은 다음과 같이 확인할 수 있습니다.
mysum.__doc__
```

```python
# 결과
'\n    이 함수는 더하기입니다.\n    a와 b를 더한 결과를 출력합니다.\n    docstring이라고 부릅니다.\n    '
```



### 코드 라인

* 기본적으로 파이썬에서는 문장 끝에 `;`을 작성하지 않음
* 한 줄로 표기할 때는 `;`를 사용하여 표기할 수 있음

```python 
# print문을 두번 써봅시다.
print('hello')
print('lee')
>>> 결과
hello
lee
```

```python
# print문을 한줄로 이어서 써봅시다. 오류 메시지를 확인해주세요.
print('hello')print('lee')
```

```
# 에러 메세지
 File "<ipython-input-8-cdc804eabc3b>", line 2
    print('hello')print('lee')
                      ^
SyntaxError: invalid syntax
```

```python
# ;을 통해 오류를 해결해봅시다.
print('hello');print('lee')
>>> 결과
hello
lee
```

* 여러줄을 한번에 작성할 땐 역슬래시 `\`를 사용하여 아래와 같이 할 수 있음.

```python
# print문을 통해 안되는 코드 예시 작성해봅시다.
print('
안녕')
```

```python
# 에러 메세지
  File "<ipython-input-10-6a6af35a2fdf>", line 2
    print('
           ^
SyntaxError: EOL while scanning string literal

```

```python
# print문을 통해 되는 코드 예시 작성해봅시다.
print('\
안녕')
>>> 안녕
```

* `[]` `{}` `()`는 `\` 없이도 가능함

```python
# list를 두 줄에 걸쳐서 만들어봅시다.
lunch = ['짜장면','짬뽕','탕수육',
        '초밥','쫄면만두']
print(lunch)
>>> 
['짜장면', '짬뽕', '탕수육', '초밥', '쫄면만두']
```



# 2) 변수(variable) 및 자료형

* 변수는 `=`을 통해 할당(assignment)됨
* 해당 자료형을 확인하기 위해서는 `type()`을 활용함
* 해당 변수의 메모리 주소를 확인하기 위해서는 `id()`를 활용함

```python
# 변수 x에 숫자를 저장하고 메모리 위치를 확인해봅시다.
x = 1
print(id(x))
# 그리고 자료형을 확인해봅시다.
print(type(x))
>>>
1376414464
<class 'int'>
```

- 같은 값을 동시에 할당할 수 있음

```python
# 같은 값을 동시에 할당해봅시다.
x = y = 2
print(x)
print(y)
>>>
2
2
```

- 다른 값을 동시에 할당 가능함

```python
# 동시에 두개의 변수에 값 두개를 할당해봅시다.
x, y = 1, 2
print(x)
print(y)
>>>
1
2
```

* 변수와 인자의 개수가 맞지 않을 때 에러를 확인

```python
# 변수의 갯수가 더 많을 때 오류를 알아봅시다.
x, y = 1
>>>
TypeError                                 Traceback (most recent call last)
<ipython-input-17-e79f419d1f6a> in <module>
      1 # 변수의 갯수가 더 많을 때 오류를 알아봅시다.
----> 2 x, y = 1

TypeError: 'int' object is not iterable

# 변수의 갯수가 더 적을 때 오류를 알아봅시다.
x, y = 1, 2, 3
>>>
ValueError                                Traceback (most recent call last)
<ipython-input-18-1acfd9ca7965> in <module>
      1 # 변수의 갯수가 더 적을 때 오류를 알아봅시다.
----> 2 x, y = 1, 2, 3

ValueError: too many values to unpack (expected 2)
```

* 이를 활용하면 서로 값을 바꾸고 싶은 경우 아래와 같이 활용 가능함

```python
# 변수 x와 y의 값을 바꿔봅시다.
print(x, y)
x, y = y, x
print(x, y)
>>>
1 2
2 1
```



## 1. 수치형

####  `int` 정수

* 모든 정수는 `int`로 표현
* 파이썬 3.x 버전에서는 `long` 타입은 없고 모두 `int` 형으로 표기 됨
* 10진수가 아닌 8진수 : `0o`/2진수 : `0b` /16진수: `0x`로도 표현 가능함

```python
# python 3.x에서 long은 없어졌습니다.
a = 3**1000
print(a)
print(type(a))
>>> 결과
1322070819480806636890455259752144365965422032752148167664920368226828597346704899540778313850608061963909777696872582355950954582100618911865342725257953674027620225198320803878014774228964841274390400117588618041128947815623094438061566173054086674490506178125480344405547054397038895817465368254916136220830268563778582290228416398307887896918556404084898937609373242171846359938695516765018940588109060426089671438864102814350385648747165832010614366132173102768902855220001
<class 'int'>
```

```python
# 파이썬에서 가장 큰 숫자를 활용하기 위해 sys 모듈을 불러옵니다.
import sys
sys.maxsize
print(type(sys.maxsize))
>>> 결과
<class 'int'>
```

- 파이썬에서 정수는 overflow(오버플로우)가 발생하지 않음
- arbitrary-precision arithmetic으로 정수를 처리하기 때문임



####  `float`(부동소수점, 실수)

* 실수는 `float`로 표현됨

```python
# 변수에 실수를 넣고 해당 변수 type 확인
a = 1.12
print(a)
print(type(a))
>>> 결과
1.12
<class 'float'>
```

- 실수의 경우 실제로 값을 처리하기 위해서는 조심할 필요가 있음

```python
# 실수의 덧셈
2.5 + 3.7
>>>
6.2
# 실수의 뺄셈
3.5 - 3.12
>>>
0.3799999999999999
# 우리가 원하는대로 반올림
round(3.5 - 3.12, 2)
>>>
0.38
# 두 개의 값이 같은지 확인
a = 3.5 - 3.12
b = 0.38
a == b
>>>
False
```

* 다음과 같은 방법으로 처리 가능

```python
# 기본적인 처리방법
# 내가 허용하는 정말 작은 수보다 작은가
abs(a-b) <= 1e-10
>>>
True

# sys 모듈을 통해 처리하는 방법
import sys
abs(a - b) <= sys.float_info.epsilon
>>>
True

print(sys.float_info.epsilon)
>>>
2.220446049250313e-16

# python 3.5부터 활용 가능한 math 모듈을 통해 처리하는 법
import math
math.isclose(a, b)
>>>
True
```



####  `complex` (복소수)

* 복소수는 허수부를 `j`로 표현한다. 

```python
# 변수에 복소수를 넣고 해당 변수의 type을 알아봅시다.
#i쓰면 오류
a = 3 + 4j
type(a)
>>>
complex

# 복소수와 관련된 메소드들을 확인해봅시다.
print(a.imag)
print(a.real)
print(a.conjugate())
>>>
4.0
3.0
(3-4j)
```



## 2. Bool

* 파이썬에는 `True`와 `False`로 이뤄진 `bool` 타입이 있음

* 비교/논리 연산을 수행 등에서 활용함

* 다음은 `False`로 변환

  > 0, 0.0, (), [], {}, '', None

  

### 3. None

* 파이썬에서는 값이 없음을 표현하기 위해 `None`타입이 존재함

```python
# None의 타입을 알아봅시다.
type(None)
>>>
NoneType

# 변수에 저장해서 확인해봅시다.
# 초기화된 변수 생성
z = None
print(z)
>>>
None
```



### 4. 문자열(String)

* Single quotes(`'`)나 Double quotes(`"`)을 활용하여 표현 가능함
* 단, 문자열을 묶을 때 동일한 문장부호를 활용해야하며, `PEP-8`에서는 **하나의 문장부호를 선택**하여 유지하도록 하고 있음(Pick a rule and Stick to it)

```python
# 변수에 문자열을 넣고 출력해봅시다.
name = 'minji'
print(name)
>>>
minji
```

* 다만 문자열 안에 문장부호(`'`, `"`)가 활용될 경우 이스케이프 문자(`\`)를 사용하는 것 대신 활용 가능

```python
# 문자열 안에 문장부호를 활용해서 오류를 확인해봅시다.
print('나는 생각했다.'배고프다'')
>>>
  File "<ipython-input-56-2889e241ebe1>", line 2
    print('나는 생각했다.'배고프다'')
                       ^
SyntaxError: invalid syntax
    
# 오류를 이스케이프 문자와 서로 다른 문장부호를 통해 해결해봅시다.
print('나는 생각했다. \'배고프다\'')
print("나는 생각했다. '배고프다'")
>>>
나는 생각했다. '배고프다'
나는 생각했다. '배고프다'
```

* 여러줄에 걸쳐있는 문장은 다음과 같이 표현 가능. `PEP-8`에 따르면 이 경우에는 반드시 `"""`를 사용

#### 이스케이프 문자열

* 문자열을 활용하는 경우 특수문자 혹은 조작을 하기 위하여 사용되는 것으로 `\`를 활용하여 이를 구분

| <center>예약문자</center> |   내용(의미)    |
| :-----------------------: | :-------------: |
|            \n             |     줄바꿈      |
|            \t             |       탭        |
|            \r             |   캐리지리턴    |
|            \0             |    널(Null)     |
|           `\\`            |       `\`       |
|            \\'            | 단일인용부호(') |
|            \\"            | 이중인용부호(") |

```python
# 이스케이프 문자열을 조합하여 프린트해봅시다.
print('안녕\t안녕\n슬래시출력\\')
>>>
안녕	안녕
슬래시출력\

# print를 하는 과정에서도 이스케이프 문자열을 활용 가능합니다.
# 디폴트는 \n
print('안녕',end = '\t')
print('안녕',end = '\t')
>>>
안녕	안녕

# 물론, end 옵션은 이스케이프 문자열이 아닌 다른 것도 가능합니다.
# 조합해서 프린트할 때 end
print('안녕',end = '!!')
print('안녕',end = '!!')
print('안녕',end = '!!')
>>>
안녕!!안녕!!안녕!!
```

#### 예제

>다음의 문장을 출력해보세요.
>
>- `"""` 사용 금지
>- `print` 여러번 사용 금지
>
>> "파일은 C:\Windows\Users\내문서\Python에 저장이 되어있습니다."
>> 나는 생각했다. 'cd를 써서 git bash로 들어가봐야지'

```python
# 여기에 코드를 작성해주세요.
print('\"파일은 C:\\Windows\\Users\\내문서\\Python에 저장이 되어있습니다.\"나는 생각했다. \'cd를 써서 git bash로 들어가봐야지\'')
>>>
"파일은 C:\Windows\Users\내문서\Python에 저장이 되어있습니다."나는 생각했다. 'cd를 써서 git bash로 들어가봐야지'
```

### String interpolation

* `%-formatting`
* [`str.format()`](https://pyformat.info/)
* [`f-strings`](https://www.python.org/dev/peps/pep-0498/) : 파이썬 3.6 버전 이후에 지원 되는 사항입니다.
* f-strings에서는 형식을 지정할 수 있음

```python
# 다양한 형식을 활용하기 위해 datetime 모듈로 오늘을 표현해봅시다.
import datetime
today = datetime.datetime.now()
print(today)
>>>
2019-01-02 11:36:21.189136
```

* 연산과 출력 형식 지정도 가능

```python
# string interpolation에서 연산과 숫자 출력형식을 지정해봅시다.
pi = 3.141592
print(f'{pi:.3}, 반지름이 2일 때 원의 넓이는 {pi*2*2}')
>>>
3.14, 반지름이 2일 때 원의 넓이는 12.566368
```

## 연산자

#### 산술 연산자

* Python에서는 기본적인 사칙연산 가능함

| 연산자 | 내용           |
| ------ | -------------- |
| +      | 덧셈           |
| -      | 뺄셈           |
| \*     | 곱셈           |
| /      | 나눗셈         |
| //     | 몫             |
| %      | 나머지(modulo) |
| \*\*   | 거듭제곱       |

#### 비교 연산자

* 수학에서 배운 연산자와 동일하게 값 비교 가능

| 연산자 | 내용     |
| ------ | -------- |
| a > b  | 초과     |
| a < b  | 미만     |
| a >= b | 이상     |
| a <= b | 이하     |
| a == b | 같음     |
| a != b | 같지않음 |

#### 논리 연산자

| 연산자  | 내용                         |
| ------- | ---------------------------- |
| a and b | a와 b 모두 True시만 True     |
| a or b  | a 와 b 모두 False시만 False  |
| not a   | True -> False, False -> True |

* 우리가 알고 있는 `&`, `|`은 파이썬에서 비트 연산자임
* 파이썬에서 and는 a가 거짓이면 a를 리턴하고, 참이면 b를 리턴
* 파이썬에서 or은 a가 참이면 a를 리턴하고, 거짓이면 b를 리턴

#### 복합 연산자

* 복합 연산자는 연산과 대입이 함꼐 이뤄짐
* 반복ㅁ문을 통해서 갯수를 카운트할 때 가장 많이 활용됨

| 연산자    | 내용       |
| --------- | ---------- |
| a += b    | a = a + b  |
| a -= b    | a = a - b  |
| a \*= b   | a = a \* b |
| a /= b    | a = a / b  |
| a //= b   | a = a // b |
| a %= b    | a = a % b  |
| a \*\*= b | a = a ** b |

#### 기타 연산자

* Concatenation : 숫자가 아닌 자료형은 `+` 연산자를 통해 합칠 수 있음
* Containment Test : `in` 연산자를 통해 속해있는지 여부를 확인할 수 있음
* Identity : `is`연산자를 통해 동일한 object인지 확인할 수 있음
* Indexing/Slicing : `[]`를 통한 값 접근 및 `[:]`를 통한 슬라이싱

```python
# 파이썬에서 -5부터 256까지의 숫자는 메모리에 동일하게 저장되어 있음
# 그래서 그 범위 내의 숫자를 대입하면 id가 같게 나오지만 범위 밖의 숫자를 대입하면 id가 다르게 나옴
a = 4
b = 4
print(a is b)
print(id(a))
print(id(b))
>>>
True
1376414560
1376414560

a = 257
b = 257
print(a is b)
print(id(a))
print(id(b))
>>>
False
2817041802736
2817041802416
```

#### 연산자 우선순위

1. `()`을 통한 grouping
2. Slicing
3. Indexing
4. 제곱연산자 **
5. 단항연산자 +, - (음수/양수 부호)
6. 산술연산자 *, /, %
7. 산술연산자 +, -
8. 비교연산자, `in`, `is`
9. `not`
10. `and`
11. `or`



## 기초 형변환(Type conversion, Typecasting)

* 파이썬에서 데이터타임은 서로 변환할 수 있음

### 암시적 형 변환(Implicit Type Conversion)

* 사용자가 의도하지 않았지만 파이썬 내부적으로 자동으로 형변환하는 경우
* bool, Numbers(int, float, complex)

```python
# int와 complex를 더해봅시다. 그 결과의 type은 무엇일까요?
print(int_num + complex_num)
print(type(int_num + complex_num))
# 더 큰 타입인 complex로 변환
>>>
(6+4j)
<class 'complex'>
```

### 명시적 형변환(Explicit Type Conversion)

위의 상황을 제외하고는 모두 명시적으로 형 변환 필요

- string -> intger : 형식에 맞는 숫자만 가능
- integer -> string : 모두 가능

암시적 형변환이 되는 모든 경우도 명시적으로 형변환 가능

- `int()` : string, float를 int로 변환
- `float()` : string, int를 float로 변환
- `str()` : int, float, list, tuple, dictionary를 문자열로 변환

# 시퀀스(sequence) 자료형

`시퀀스`는 데이터의 순서대로 나열된 형식을 나타냄

1. 리스트(list)

2. 튜플(tuple)

3. 레인지(range)

4. 문자열(string)

5. 바이너리(binary)

### 1. `list`

* 리스트는 대괄호 `[]`를 통해 만들 수 있음
* 값에 대한 접근은 `list[i]`를 통해 함

### 2. `tuple`

* 리스트와 유사하지만 `()`로 묶어서 표현
* tuple은 수정이 불가능(immutable)하고 읽기만 할 수 있음
* 직접 사용하는 것 보다는 파이썬 내부에서 사용

### 3. `range()`

* 숫자의 시퀀스를 나타내기 위해 사용

* 기본형 : `range(n)`

  > 0 부터 n-1까지 값을 가짐

* 범위 지정 : `range(n, m)`

  > n부터 m-1까지 값을 가짐

* 범위 및 스텝 지정 : `range(n, m, s)`

  > n부터 m-1까지 +s만큼 증가

#### 시퀀스에서 활용할 수 있는 연산자 / 함수

| operation  | 설명                    |
| ---------- | ----------------------- |
| x in s     | containment test        |
| x not in s | containment test        |
| s1 + s2    | concatenation           |
| s * n      | n번만큼 반복하여 더하기 |
| s[i]       | indexing                |
| s[i:j]     | slicing                 |
| s[i:j:k]   | k간격으로 slicing       |
| len(s)     | 길이                    |
| min(s)     | 최솟값                  |
| max(s)     | 최댓값                  |
| s.count(x) | x의 갯수                |

# set, dictionary

* `set`과 `dictionary`는 기본적으로 순서가 없음

#### 1. `set`

* 세트는 수학에서 집합과 동일하게 처리
* 중괄호 `{}`를 통해 만들고 순서 없고 중복된 값이 없음

| 연산자/함수       | 설명   |
| ----------------- | ------ |
| a - b             | 차집합 |
| a \| b            | 합집합 |
| a & b             | 교집합 |
| a.difference(b)   | 차집합 |
| a.union(b)        | 합집합 |
| a.intersection(b) | 교집합 |

* `set`을 활용하면 `list`의 중복된 값을 손쉽게 제거할 수 있음

#### 2. `dictionary`

* 딕셔너리는 `key`와 `value`가 쌍으로 이뤄져있음
* `{}`를 통해`dict()`로 만들 수 있음
* `key`는 immutable한 모든 것이 가능함(불변값 : string, integer, float, boolean, tuple, range)
* `value`는 `list`, `dictionary`를 포함한 모든 것이 가능함





