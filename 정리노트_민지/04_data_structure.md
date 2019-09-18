# data_structure

# 1 문자열 메소드 활용

* 문자열은 변하지 않음
* 어떤 값을 변형할 때 아래의 메소드 말고는 변형할 수 없음
* 추가와 삭제 불가능함

> 메소드 = 클래스의 함수
>
> ex) 딕셔너리에 딸려있는 함수

## 1. 변형

### 1)  `.capitalize()`, `title()`, `.upper()`

* `.capitalise()` : 앞글자를 대문자로 만들어 반환, 나머지는 소문자로 반환
* `.title() `: 어포스트로피(`)나 공백 이후를 대문자로 만들어 반환.(띄어쓰기가 있을 때마다 대문자로 반환)
* `upper()` : 모두 대문자로 만들어서 반환



### 2) `lower()`, `swapcase()`

* `lower()` : 모두 소문자로 만들어서 반환
* `swapcase()` : 대문자는 소문자로, 소문자는 대문자로 변경하여 반환



### 3) `.join(iterable)`

* 특정한 문자열로 만들어서 반환

```python
",".join('abcd')
>>> 'a, b, c, d'

''.join(['hi', 'everyone'])
>>> 'hieveryone'

a = [1, 2, 3]
b = ''.join(map(str, a))
print(b)
print(type(b))
>>>
123
<class 'str'>

c = ''.join(['1', '2', '3', '4'])
print(c)
print(type(c))
>>> 
1234
<class 'str'>
```



### 4) `.replace(old, new[, count])`

* 대괄호([])는 선택해서 입력하는 것으로 필수로 입력하지 않아도 괜찮음
* 바꿀 대상의 글자를 새로운 글자로 바꿔서 변환
* count를 지정하면 해당 횟수만큼만 시행



### 5) 글씨제거(`strip[chars]`)

* 특정한 문자들을 지정하면 양쪽을 제거하거나 왼쪽을 제거하거나(lstrip), 오른쪽을 제거(rstrip)
* 지정하지않으면 공백을 제거



## 2. 탐색 및 검증

### 1) `.find(x)` 

* x의 첫번째 위치를 반환. 없으면 -1을 반환



### 2) `.index(x)` 

* x의 첫번쨰 위치를 반환. 없으면 에러 발생



### 3) 다양한 확인 메소드 : 참/ 거짓 반환

* `.isalpha()` : 알파벳인지 확인
* `.isdecimal()` : 숫자(10진수)인지 확인
* `.indigit()` :숫자(10진수)인지 확인
* `.isnumeric()` :숫자인지 확인
* `.isspace()` :공백인지 확인
* `.issuper()` : 대문자인지 확인
* `.istitle()` :title형식(단어마다 첫글자가 대문자)인지 확인
* `.islower()` : 소문자인지 확인



### 4) `split()` 

* 문자열을 특정한 단위로 나눠 리스트로 변환

```python
inputs1 = input().split()
print(inputs1)
print(type(inputs1))
print(type(inputs1[0]))
>>>
1 3 5 7 9
['1', '3', '5', '7', '9']
<class 'list'>
<class 'str'>

inputs2 = list(map(int, input().split()))
print(inputs2)
print(type(inputs2))
print(type(inputs2[0]))
>>>
2 4 6 8 0
[2, 4, 6, 8, 0]
<class 'list'>
<class 'int'>
```



### 5) 문자열 뒤집기

* [::-1]

```python
'123'[::-1]
>>>
'321'
```

* .join

```python
''.join(reversed('123'))
>>>
'321'
```



# 2 리스트 메소드 활용

## 1. 값 추가 및 삭제

### 1) `.append(x)`

* 리스트에 값을 추가할 수 있음



### 2) `extend(iterable)`

* 리스트에 iterable(list, range, tuple, string)값을 붙일 수 있음



### 3) `insert(i, x)`

* 정해진 위치 `i`에 `x`를 추가



### 4) `remove(x)`

* 리스트에서 값이 x인 것을 삭제
* 값을 반환해주지 않으므로 print로 계속 확인 필요
* 값이 지워지면 다시 돌릴 수 없는 메소드이므로 주의가 필요함



### 5) `.pop(i)`

* 정해진 위치 `i`에 있는 값을 삭제하며 그 항목을 반환
* `i`가 지정되지 않으면 마지막 항목을 삭제하고 반환
* 특정 인덱스를 지정해서 지워나갈 때 사용



## 2. 탐색 및 정렬

### 1) `.index(x)`

* 원하는 값을 찾아 index값을 반환



### 2) `.count(x)`

* 원하는 값의 갯수를 확인



### 3) `.sort()`

* 리스트의 값들을 오름차순으로 정렬
* `sorted()`와는 다르게 원본 리스트를 변형시키고 None를 반환
* sort()보다는 sorted를 써서 정렬된 리스트를 다른 값에 저장해서 사용하는 것이 안전



### 4)`.reverse()`

* 리스트를 반대로 뒤집음
* 정렬이 아니므로 헷갈리지 않게 유의해서 사용할 것!



## 3. 복사

* 파이썬에서 값을 변경할 수 없는 숫자나 문자열은 값을 복사함
* 리스트는 값을 변경할 수 있어서 값 자체를 복사하지 않고 값이 저장되어있는 주소를 복사해오기 때문에 값을 변경해도 주소가 같음
* 숫자나 문자열을 값을 변경할 수 없어서 값 자체를 복사하기 때문에 값을 변경하면 주소가 달라지는 것을 확인할 수 있음

```python
# 리스트를 복사
a = [1, 2, 3]
b = a
# b의 값을 바꾸고 a를 출력
b[0] = 5
print(a)
>>>
[5, 2, 3]
# a와 b의 값과 주소가 같은지 확인
print(a)
print(b)
print(id(a))
print(id(b))
>>>
[5, 2, 3]
[5, 2, 3]
2364435699144
2364435699144
```

```python
# 숫자를 복사
a = 10005
b = a
# b의 값을 바꾸고 a를 출력
b = 1004
print(a)
>>>
10005

# a와 b의 값과 주소가 같은지 확인
print(a)
print(b)
print(id(a))
print(id(b))
>>>
10005
1004
37334768
37332080

```

* 따라서 리스트처럼 변경가능한(mutable)자료형을 복사할 때는 다음과 같이 해야함

```python
# 방법 1
a = [1, 2, 3]
b = a[:]
b[0] = 5
print(a)
print(b)
print(id(a))
print(id(b))

>>>
[1, 2, 3]
[5, 2, 3]
40557384
40556872


# 방법 2
a = [1, 2, 3]
b = list(a)
b[0] = 5
print(a)
print(b)
print(id(a))
print(id(b))

>>>
[1, 2, 3]
[5, 2, 3]
40557768
40591048
```

* 하지만 이렇게 하는 것도 일부 상황에서만 서로 다른 얕은 복사(shallow copy)임
* mutable 객체 안에 mutable객체인 경우에는 문제가 생김

```python
# 방법 1
a = [[1, 2], 2, 3]
b = a[:]
b[0][0] = 5
print(id(a[0]))
print(id(b[0]))
>>>
42851144
42851144

# 방법 2
a = [[1, 2], 2, 3]
b = list(a)
b[0][0] = 5
print(id(a[0]))
print(id(b[0]))
>>>
42850760
42850760
```

* id(a)와 id(b)값은 다르지만 그 내부의 객체 id(a[0])과 id(b[0])은 같은 주소임
* a[1]의 값을 변경하면 b[1]의 값도 같이 변경됨

```python
# 방법 1
a = [[1, 2], [2, 3]]
b = a[:]
a[1].append(5)
print(a)
print(b)
print(id(a[1]))
print(id(b[1]))
>>>
[[1, 2], [2, 3, 5]]
[[1, 2], [2, 3, 5]]
42654024
42654024

# 방법 2
a = [[1, 2], [2, 3]]
b = list(a)
a[1].append(5)
print(a)
print(b)
print(id(a[1]))
print(id(b[1]))
>>>
[[1, 2], [2, 3, 5]]
[[1, 2], [2, 3, 5]]
42688328
42688328
```

* copy 모듈의 copy 메소드도 얕은 복사

```python
import copy
a = [[1, 2], [2, 3]]
b = copy.copy(a)
a[1].append(5)
print(a)
print(b)
print(id(a[1]))
print(id(b[1]))
>>>
[[1, 2], [2, 3, 5]]
[[1, 2], [2, 3, 5]]
43374280
43374280
```



### 깊은 복사**(deep copy)

* 중첩된 상황에서 복사할 때 사용
* 내부에 있는 모든 객체까지 새롭게 값이 변경됨

```python
import copy

a = [[1, 2], [2, 3]]
b = copy.deepcopy(a)
a[1].append(5)
print(a)
print(b)
print(id(a[1]))
print(id(b[1]))
>>>
[[1, 2], [2, 3, 5]]
[[1, 2], [2, 3]]
43374280
43375304
```



### 얕은 복사와 깊은 복사 차이점**

* 얕은 복사는 일차원적으로 주소를 카피하는 것
* 깊은 복사는 반복문을 돌면서 하나씩 꺼내서 새로 만드는 것
* 중첩된 것을 복사하고 싶으면 깊은 복사를, 숫자나 스트링처럼 일차원적인 값을 복사하고 싶을 땐 앝은 복사를 하는 것이 좋음



## 4. 삭제 `clear()`

* 리스트의 모든 항목을 삭제



# 3 List Comprehension

## 1. 사전 준비

> 다음의 리스트를 만들어보세요

1. 1 ~ 10 까지의 숫자 중 짝수만 담긴 리스트 `even_list`
2. 1 ~ 10 까지의 숫자를 세제곱한 값이 담긴 리스트 `cubic_list`

```python
even_list = []
cubic_list = []
for i in range(0, 11):
    if not i % 2:
        even_list.append(i)
    cubic_list.append(i ** 3)
print(even_list)
print(cubic_list)
>>>
[0, 2, 4, 6, 8, 10]
[0, 1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
```

* list comprehension을 사용해서 여러개의 `for` 문과 `if`문을 중첩적으로 사용하면 코드를 간단하게 만들 수 있음

```python
even_list = [x for x in range(0, 11) if not x % 2]
cubic_list = [x ** 3 for x in range(0, 11) ]
```



#### 실습1. 짝짓기

> 주어진 두 list의 가능한 모든 조합을 담은 `pair`리스트를 만들어주세요

1. 반복문 활용
2. list comprehension 활용

girls = ['jane', 'iu', 'mary']
boys = ['justin', 'david', 'kim']

예시 출력)

[('justin', 'jane'), ('justin', 'iu'), ('justin', 'mary'), ('david', 'jane'), ('david', 'iu'), ('david', 'mary'), ('kim', 'jane'), ('kim', 'iu'), ('kim', 'mary')]

```python
girls = ['jane', 'iu', 'mary']
boys = ['justin', 'david', 'kim']
pair = []
for girl in girls:
    for boy in boys:
        pair.append((girl, boy))
print(pair)
>>>
[('jane', 'justin'), ('jane', 'david'), ('jane', 'kim'), ('iu', 'justin'), ('iu'
, 'david'), ('iu', 'kim'), ('mary', 'justin'), ('mary', 'david'), ('mary', 'kim'
)]
```

```python
girls = ['jane', 'iu', 'mary']
boys = ['justin', 'david', 'kim']
pair = [(girl, boy) for girl in girls for boy in boys]
print(pair)
>>>
[('jane', 'justin'), ('jane', 'david'), ('jane', 'kim'), ('iu', 'justin'), ('iu'
, 'david'), ('iu', 'kim'), ('mary', 'justin'), ('mary', 'david'), ('mary', 'kim'
)]
```



#### 실습2. 피타고라스 정리

> 주어진 조건(x < y < z < 50) 내에서 피타고라스 방정식의 해를 찾아보세요.

1. 반복문 활용
2. list comprehension 활용

예시 출력)
[(3, 4, 5), (5, 12, 13), (6, 8, 10), (7, 24, 25), (8, 15, 17), (9, 12, 15), (9, 40, 41), (10, 24, 26), (12, 16, 20), (12, 35, 37), (15, 20, 25), (15, 36, 39), (16, 30, 34), (18, 24, 30), (20, 21, 29), (21, 28, 35), (24, 32, 40), (27, 36, 45)]

```python
pytha = []
for x in range(1, 50):
    for y in range(x, 50):
        for z in range(y, 50):
            if x ** 2 + y ** 2 == z ** 2:
                pytha.append((x, y, z))
print(pytha)
>>>
[(3, 4, 5), (5, 12, 13), (6, 8, 10), (7, 24, 25), (8, 15, 17), (9, 12, 15), (9,
40, 41), (10, 24, 26), (12, 16, 20), (12, 35, 37), (15, 20, 25), (15, 36, 39), (
16, 30, 34), (18, 24, 30), (20, 21, 29), (21, 28, 35), (24, 32, 40), (27, 36, 45
)]
```

```python
pytha = [(x, y, z)  for x in range(1, 50) for y in range(x, 50) for z in range(y, 50) if x ** 2 + y ** 2 == z ** 2]
print(pytha)
>>>
[(3, 4, 5), (5, 12, 13), (6, 8, 10), (7, 24, 25), (8, 15, 17), (9, 12, 15), (9,
40, 41), (10, 24, 26), (12, 16, 20), (12, 35, 37), (15, 20, 25), (15, 36, 39), (
16, 30, 34), (18, 24, 30), (20, 21, 29), (21, 28, 35), (24, 32, 40), (27, 36, 45
)]
```



#### 실습3. 모음 제거하기

> 다음의 문장에서 모음(a, e, i, o, u)를 모두 제거하시오.

1. list comprehension만 사용해보세요.

words = 'Life is too short, you need python!'

예시출력)
Lf s t shrt, y nd pythn!

```python
words = 'Life is too short, you need python!'
vowel = 'aeiou'
result = [x for x in words if x not in vowel]
print(''.join(result))
>>>
Lf s t shrt, y nd pythn!

```



# 4 딕셔너리 메소드 활용

# 1. 추가 및 삭제

## 1) `.pop(key[, default])`

* key가 딕셔너리에 있으면 제거하고 그 값을 반환
* 그렇지 않으면 설정해둔 default로 반환
* default가 없는 상태에서 딕셔너리에 해당하는 key가 없으면 KeyError가 발생



### 2) `.update()`

* 값을 제공하는 key, value로 덮어씀



### 3) `.get(key[, default])`

* key를 통해 value를 가져옴
* 절대로 KeyError가 발생하지 않음 
* default는 기본적으로 None임
* 따로 값을 반환하지 않음



## 2. dicionary Comprehension

* dictionary도 comprehension을 활용하여 만들 수 있음

#### 실습1. 세제곱 구하기

```python
# 딕셔너리는 : 필요
cubic = {x:x**3 for x in range(1, 11)}
>>>
{1: 1, 2: 8, 3: 27, 4: 64, 5: 125, 6: 216, 7: 343, 8: 512, 9: 729, 10: 10
 
# 만약 :가 없으면 튜플형태로 저장(순서 없음)
cubic = {(x, x**3) for x in range(1, 11)}
 >>>
 {(7, 343), (10, 1000), (3, 27), (2, 8), (8, 512), (1, 1), (6, 216), (9, 729), (5
, 125), (4, 64)}
```

#### 실습2.미세먼지

> 미세먼지 농도가 80초과인 지역과 미세먼지 농도를 구하시오.

dusts = {'서울': 72, '경기': 82, '대전': 29, '중국': 200}

```python
result = {key: value for key, value in dusts.items() if value > 80}
>>>
{'경기': 82, '중국': 200}

# 미세먼지 농도가 80초과면 나쁨, 80이하면 보통으로 하는 value를 가지는 딕셔너리 만들기
result = {key: '나쁨' if value > 80 else '보통' for key, value in dusts.items()}
>>>
{'서울': '보통', '경기': '나쁨', '대전': '보통', '중국': '나쁨'}
```



## 3. `.map()`, `.zip()`, `.filter()`

### 1) `.map(function, iterable)`

* iterable의 모든 원소에 function을 적용한 후 그 결과를 반환
* 대표적으로 iterable한 타입 - list, dict, set, str, bytes, tuple, range
* return은 map_object형태

```python
a = [1, 2, 3]
a = ''.join(map(str, a))
print(a)
print(type(a))
print(type(a[0]))
>>>
123
<class 'str'>
<class 'str'>

a = ['1', '2', '3']
a = list(map(int, a))
print(a)
print(type(a))
print(type(a[0]))
>>>
[1, 2, 3]
<class 'list'>
<class 'int'>
```



### 2) `zip(iterables)`

* 복수 iterable한 것들을 모아줌
* 튜플의 모음으로 구성된 zip object를 반환함

```python
girls = ['jane', 'iu', 'mary']
boys = ['justin', 'david', 'kim']
list(zip(girls, boys))
>>>
[('jane', 'justin'), ('iu', 'david'), ('mary', 'kim')]
```

* 반복문에서도 사용 가능함

```python
a = '123'
b = '456'
for num1, num2 in zip(a, b):
    print(num1, num2)
>>>
1 4
2 5
3 6
```

* zip은 반드시 길이가 같을 때 사용해야 함. 길이가 다를 경우 짧은 것을 기준으로 구성함

```python
a = [1, 2, 3]
b = ['1', '2']
list(zip(a, b))
>>>
[(1, '1'), (2, '2')]
```



### 3) `filter(function, iterable)`

* iterable중 function에서 반환된 결과가 참인 것들로 구성하여 반환



# 5 세트 메소드 활용

## 1. 추가 및 삭제

### 1) `.add(elem)`

* elem을 세트에 추가



### 2) `update(*others)`

* 여러가지 값을 순차적으로 추가
* 여기서 반드시 iterable한 값을 넣어야 함



### 3) `.remove(elem)`

* elem을 세트에서 삭제
* x가 없으면 KeyError발생



### 4) `.discard(elem)`

* x를 세트에서 삭제
* x가 없어도 에러가 발생하지 않음



### 5) `.pop()`

* 임의의 원소를 제거해 반환