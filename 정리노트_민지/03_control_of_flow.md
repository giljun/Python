# control_of_flow

#  1. 조건문

* 제어문(control of Flow)은 반복문과 조건문으로 나눌 수 있음
* 순서도(FLow chart)로 표현 가능

## 조건문 문법

* `if`문은 반드시 일정한 참/거짓을 판단할 수 있는 `조건식`과 함꼐 사용됨 `if <조건식>`
* `<조건식>`이 참인 경우 `:`이후의 문장을 수행
* `<조건식>`이 거짓인 경우 `else`이후의 문장을 수행
  * 이 때 반드시 들여쓰기에 유의해야함. 파이썬에서는 코드블록을 자바나 C언어의 `{}`와 달리 **들여쓰기**로 판단하기 때문
  * 앞으로 우리는 `PEP-8`에서 권장하는 `4spaces`를 사용할 것

#### 실습1. 조건문 기초 활용

> 조건문을 통해 변수 num의 값과 홀수, 짝수 여부를 출력하세요

예시 출력) 3  

홀수입니다.

```python
num = input()
if int(num) % 2 :
    print('홀수입니다')
else:
    print('짝수입니다')
>>>
3
홀수입니다.
```



## 복수 조건문

* 2개 이상의 조건문을 활용할 경우 `elif <조건식>:`을 활용한다.

#### 실습2. 조건식 2개 이상 활용하기

> 조건문을 통해 변수 score에 따른 평점을 출력하세요.

| 점수      | 등급 |
| --------- | ---- |
| 90점 이상 | A    |
| 80점 이상 | B    |
| 70점 이상 | C    |
| 60점 이상 | D    |
| 60점 미만 | F    |

예시 출력)

B

```python
score = int(input("점수를 입력하세요: "))
if score >= 90:
    print("A")
elif score >= 80:
    print('B')
elif score >= 70:
    print('C')
elif score >= 60:
    print('D')
else:
    print('f')
>>>
점수를 입력하세요: 60
D
```



#### 실습3. 중첩 조건문 활용

> 위의 실습문제를 활용하여 95점 이상이면 "참 잘했어요"를 함께 출력해주세요.

예시 출력) A 

참 잘했어요

```python
score = int(input("점수를 입력하세요: "))
if score >= 90:
    if score >= 95:
        print('참 잘했어요')
    print("A")
elif score >= 80:
    print('B')
elif score >= 70:
    print('C')
elif score >= 60:
    print('D')
else:
    print('f')
>>>
점수를 입력하세요: 96
참 잘했어요
A
```



## 조건 표현식(Conditionam Expression)

> true_value if <조건식> else false_value

* 다른 언어에서 활용되는 삼항연산자와 같다.

```python
a = int(input("숫자를 입력하세요: "))
print('3맞음') if a == 3 else print('3아님')
>>>
숫자를 입력하세요 : 4
3아님
```

* 표현식은 보통 조건에 따라 값을 정할 때 많이 활용됨



#### 실습4. 조건표현식과 동일한 `if`문 작성하기

> 다음 코드와 동일한 `if`문을 작성해보세요

```python
num = -5
value = num if num >= 0 else 0
print(value)
```

예시 출력)  0

```python
num = -5
if num >= 0:
    value = num
else:
    value = 0
print(value)
>>> 결과
0
```



#### 실습5. 조견표현식 만들어보기

> 다음의 코드와 동일한 조건 표현식을 작성해보세요.

```python
num = 2
if num % 2 == 1:
    result = '홀수입니다.'
else:
    result = '짝수입니다.'
print(result)
```

예시 출력) 짝수입니다.

```python
num = 2
print( '홀수입니다') if num % 2 else print('짝수입니다.')
>>> 결과
짝수입니다.
```



# 반복문

## 1. `while`문

* 조건식이 참(True)인 경우 반복적으로 코드를 실행
* 반드시 종료조건 설정 필요함
* `<조건식>`이후에 반드시 `:` 이 반드시 필요하고 이후에 오는 코드 블록은  `4spaces`로 **들여쓰기**를 꼭 해줘야함



## 2. `for`문

* 정해진 범위 내(시퀀스)에서 순차적으로 코드를 실행
* `for`문은 `sequence`를 순차적으로 **variable**에 값을 바인딩하며, 코드 블록을 시행합니다.

#### 실습1.

> 반복문과 조건문만 활용하여 1~30까지 숫자 중에 홀수만 담긴 리스트를 만드세요.

list에서 값 추가는 `.append(value)`로 합니다.

```
예시 출력)
[1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29]
```

```python
a = []
for i in range(31):
    if i % 2:
        a.append(i)
print(a)
>>> 결과
[1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29]
```



### index와 함께 `for`문 활용하기

* `enumerate()`를 활용하면 추가적인 변수를 활용할 수 있음
* `enumerate()`는 파이썬 표준 라이브러리의 내장함수 중 하나임 
  * enumerate(iterable, start = 0) 에서 literable은 시퀀스, 이터레이터, 또는 이터레이션을 지원하는 다른 객체
  * 카운트와 iterable을 이터레이션해서 얻어지는 값을 포함하는 튜플을 반환

```python
enum_lunch = enumerate(lunch)
print(list(enum_lunch))
print(type(enum_lunch))
>>>
[(0, '초밥'), (1, '치킨')]
<class 'enumerate'>
```



### dictionary 반복문 활용하기

* dictionary를 `for`문을 시행시키면 key값이 반환
* dictionary의 `key`를 출력하면서 `value`에도 접근할 수 있기 때문
* dictionary의 value를 출력하기 위해서는 다음과 같이 작성

```python
lunch = {'초밥' : '11-11', '치킨' : '22-22', '김밥' : '33-33'}
for key in lunch:
    print(lunch[key])
```

* dictionary에서 `for` 활용하는 4가지 방법

> 0. dictionary (key 반복)
>
>    for key in dict:
>        print(key)
>
> 1. key 반복
>
>    for key in dict.keys():
>        print(key)
>
> 2. value 반복
>
>    for val in dict.values():
>        print(val)
>
> 3. key와 value반복
>
>    for key, val in dict.items():
>        print(key, val)



## 3. `break`, `continum`, `else`

### 1) `break`

* 반복문을 종료하는 표현



### 2) `continue`

* continue이후의 코드를 수행하지 앟고 다음 요소를 선택해 반복을 계속 수행



### 3) `else`

* 끝까지 반복문을 수행한 이후에 실행
* (`break`를 통해 중간에 종료되지 않은 경우에만 실행)