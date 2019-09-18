# Errors and Exceptions

* 발생할 수 있는 오류와 예외처리

# 1 문법 에러(Syntax Error)

* 가장 많이 만날 수 있는 에러로 발생한 `파일 이름`과 `줄`, `^`을 통해 파이썬이 읽어들일 때(parser)의 문제 발생 위치를 표현

```python
if True:
    print('참')
else
    print('거짓')
```

```
File "<ipython-input-1-ad301a5287d3>", line 4
    else
        ^
SyntaxError: invalid syntax
>>>
else다음 :가 없음
```

### 1) `EOL`

* End Of Line

```python
print('hi)
```

```python
  File "<ipython-input-2-c86c48ac0632>", line 3
    print('hi)
              ^
SyntaxError: EOL while scanning string literal
>>>
print문 안의 문장이 끝나지 않음 '가 없음
```



### 2) EOF

* End Of File

```python
print('hi'
```

```
  File "<ipython-input-3-2507fb609382>", line 3
    print('hi'
              ^
SyntaxError: unexpected EOF while parsing
>>>
print문의 괄호가 닫혀있지 않음
```

* 에러가 정확한 위치를 가리키지 않을 수 있으므로 앞 뒤 문장을 모두 확인하는 것이 좋음



# 2 예외(Exceptions)

* 문법이나 표현식이 바르게 되어있지만, 실행시 발생하는 에러
* 아래 제시된 모든 에러는 Exception을 상속받아 이뤄짐

## 1. ZeroDivisionError

```python
10 / 0
>>>
ZeroDivisionError                         Traceback (most recent call last)
<ipython-input-5-1a1c9c3dae95> in <module>
----> 1 10 / 0

ZeroDivisionError: division by zero
```



## 2. NameError

```python
print(name)
>>>
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-6-a384a4d4f00c> in <module>
----> 1 print(name)

NameError: name 'name' is not defined
```



## 3. TypeError

```python
1 + '1'
>>>
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-7-a8978fdced50> in <module>
----> 1 1 + '1'

TypeError: unsupported operand type(s) for +: 'int' and 'str'
```



* 함수 호출 과정

```python
round('24.5')
>>>
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-9-07903be13ecd> in <module>
----> 1 round('24.5')

TypeError: type str doesn't define __round__ method
```



* 필수 argument 누락

```python
import random
random.sample([1, 2])
>>>
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-10-ffa63ee9bdc0> in <module>
      1 import random
----> 2 random.sample([1, 2])

TypeError: sample() missing 1 required positional argument: 'k'
```



* argument가 많은 경우

```python
random.choice([1, 2], 1)
>>>
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-11-f207298f5559> in <module>
----> 1 random.choice([1, 2], 1)

TypeError: choice() takes 2 positional arguments but 3 were given
```



## 4. ValueError

* 타입은 맞는데 값이 다르게 된 경우

```python
int('3.5')
>>>
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-13-8ff441dde884> in <module>
----> 1 int('3.5')
      2 int(3.5)

ValueError: invalid literal for int() with base 10: '3.5'
```



* 리스트에서 값이 적절하지 않은 경우

```python
a = [1, 2, 3]
a.index(100)
>>>
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-14-eaf459ec9a4f> in <module>
      1 a = [1, 2, 3]
----> 2 a.index(100)

ValueError: 100 is not in list
```



## 5. IndexError

* 리스트에서 값이 적절하지 않은 경우

```python
a = [1, 2, 3]
a[6]
>>>
---------------------------------------------------------------------------
IndexError                                Traceback (most recent call last)
<ipython-input-15-88fe2de15d6a> in <module>
      1 a = [1, 2, 3]
----> 2 a[6]

IndexError: list index out of range
```



 ## 6. KeyError

```python
song_list = {'sia' : 'candy cane lane'}
song_list['queen']
>>>
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-16-caa678999b84> in <module>
      2 song_list = {'sia' : 'candy cane lane'}
----> 3 song_list['queen']

KeyError: 'queen'
```



 ## 7. ModuleNotFoundError

```python
import randome
>>>
---------------------------------------------------------------------------
ModuleNotFoundError                       Traceback (most recent call last)
<ipython-input-17-8ef81c8b686f> in <module>
----> 1 import randome

ModuleNotFoundError: No module named 'randome'
```



## 8. ImportError

```python
from bs4 import bs
>>>
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)
<ipython-input-18-eb0237bb1870> in <module>
----> 1 from bs4 import bs

ImportError: cannot import name 'bs'
```



## 9. KeyboardInterrupt

* 사용자가 키보드로 중지했을 때 발생

```python
while True:
    pass
>>>
---------------------------------------------------------------------------
KeyboardInterrupt                         Traceback (most recent call last)
<ipython-input-19-a8d0705db4bb> in <module>
      1 while True:
----> 2     pass

KeyboardInterrupt: 
```

 

# 3 예외 처리

## 1. 기본 - `try` `except`

* `try`구문을 이용하여 예외처리를 할 수 있음
* 기본은 다음과 같은 구조를 가짐

```python
try:
    codeblock1
except 예외:
    codeblock2
```

* `try`절이 실행
* 예외가 발생하지 않으면 `except`없이 실행이 종료
* 예외가 중간에 발생하면 , 남은 부분을 수행하지 않고 `except`가 실행

```python
try:
    num = input('값을 입력하세요: ')
    print(int(num))
    print(num)
except ValueError:
    print('정수를 입력하세요')
>>>
값을 입력하세요: d
정수를 입력하세요
```



## 2. 복수의 예외처리

* 두 가지 예외를 모두 처리할 수 있음

  try:
      codeblock1
  except (예외1, 예외2):
      codeblock2

* 문자열일 때와 0 일 때 모두 예외 처리

```python
try:
    num = input('입력: ')
    print(100 / int(num))
except (ValueError, ZeroDivisionError):
    print('다시 입력해주세요')
>>>
입력: d
다시 입력해주세요
```



* 각각 다른 오류를 출력할 수 있음

```python
try:
    num = input('입력: ')
    print(100 / int(num))
except ValueError:
    print('정수를 입력해주세요')
except ZeroDivisionError:
    print('다시 입력해주세요')
```



* 에러는 순차적으로 수행되니까 가장 작은 범주부터 시작해야 함

```python
try:
    num = input('입력: ')
    print(100 / int(num))
except Exception:
    print('오류')
except ZeroDivisionError:
    print('다시 입력해주세요')
>>>
입력: 0
오류
```



## 3. 에러 문구 처리

* 에러 문구를 함께 넘겨줄 수 있음

  try:
      codeblock1
  except 예외 as e:
      codeblock2

```python
try:
    num = input('입력: ')
    print(100 / int(num))
except ValueError as e:
    print(f'정수를 입력해주세요 {e}')
except ZeroDivisionError as e:
    print(f'다시 입력해주세요 {e}')
>>>
입력: d
정수를 입력해주세요  invalid literal for int() with base 10: 'd'
```



## 4. `else`

* 에러가 밠생하지 않는 경우 수행되는 문장

  try:
      codeblock1
  except 예외:
      codeblock2
  else:
      codeblock3

```python
try:
    a = [1, 2, 3]
    b = a[1]
except IndexError:
    print('index오류 발생')
else:
    print(b * 1000)
>>>
2000
```



## 5. `finally`

* 반드시 수행해야하는 문장

  try:
      codeblock1
  except 예외:
      codeblock2
  finally:
      codeblock3

```python
try:
    a = {'python' : 100, 'java' : 100}
    a['html']
except KeyError as e:
    print(f'키 에러 발생 {e}')
finally:
    print(a)
>>>
키 에러 발생 'html'
{'python': 100, 'java': 100}
```



# 4 예외 발생시키기

```python
raise ValueError
>>>
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-9-1cbbb0c66c9b> in <module>
      1 # 오류를 발생시켜 봅시다.
----> 2 raise ValueError

ValueError: 
```



* 인자를 넘겨줄 수 있음

```python
raise ValueError('코드 잘짜자')
>>>
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-11-09b95d18a125> in <module>
----> 1 raise ValueError('코드 잘짜자')

ValueError: 코드 잘짜자
```

 

#### 실습1. 

> 양의 정수 두 개를 받아 몫과 나머지로 출력하는 함수를 만들어보세요.

`def my_div(num1,num2)`

- num2가 0이여서 발생하는 오류인 경우 **에러메시지**를 출력해주세요.

  예) division by zero 오류가 발생하였습니다.

- 인자가 string이여서 발생하는 경우는 **ValueError와 함께 '숫자를 넣어주세요'를 출력**해주세요. (실제로 이 경우에 발생하는 것은 TypeError입니다.)
- 정상적인 경우에는 결과를 return합니다.

```python
def my_div(num1, num2):
    try:
        q, r = num1//num2, num1%num2
    except ZeroDivisionError as e:
        print(f'{e} 오류가 발생했음')
    except:
        raise ValueError('숫자를 넣어주세요!')
        print('hi')
    else:
        return q, r
```

```python
if True
    print('hi')
    
a = 3 + 2
b = 5 + 3
print(a + b )
>>>
  File "<ipython-input-14-7e403567346a>", line 1
    if True
           ^
SyntaxError: invalid syntax
```



# 5 `assert`

* `assert` 문은 예외를 발생시키는 다른 방법

* 보통 상태를 검증하는데 사용되며 무조건 `AssertionError`가 발생

  `assert Boolean expression, error message`

* 위의 검증식이 거짓일 경우 발생

* `raise`는 항상 예외를 발생시키고, `assert`는 지정한 예외가 발생한다는 점에서 다름



#### 실습

>양의 정수 두개를 받아 몫과 나머지로 출력하는 함수를 만들어보세요.

`def my_div(num1,num2)`

- assert를 활용하여, int가 아닌 경우 AssertionError 발생

```python
def my_div(num1, num2):
    assert type(num1) == int and type(num2) == int, '숫자를 입력하지 않았습니다.'
    try:
        result = num1/num2
    except ZeroDivisionError as e:
        print(f'{e}, 0으로 나누지마')
    else:
        return result
```

```python
my_div('1', '2')
>>>
---------------------------------------------------------------------------
AssertionError                            Traceback (most recent call last)
<ipython-input-58-cd1e2b9ba8ef> in <module>
----> 1 my_div('1', '2')

<ipython-input-57-be4106635d97> in my_div(num1, num2)
      1 def my_div(num1, num2):
----> 2     assert type(num1) == int or type(num2) == int, '숫자를 입력하지 않았습니다.'
      3     try:
      4         result = num1/num2

AssertionError: 숫자를 입력하지 않았습니다.
```

