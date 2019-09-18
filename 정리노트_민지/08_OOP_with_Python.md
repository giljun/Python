# OOP_with_Python

## 1. 용어 정리

```python
class Person:                       #=> 클래스 정의(선언) : 클래스 객체 생성
    name = '홍길동'                  #=> 멤버 변수(데이터 어트리뷰트/데이터 속성)
    def greeting(self):             #=> 멤버 메서드(메서드)
        print(f'{self.name}')
        
iu = Person()       # 인스턴스 객체 생성 이름이 iu, person속성 가짐
daniel = Person()   # 인스턴스 객체 생성
iu.name             # 데이터 어트리뷰트 호출
iu.greeting()       # 메서드 호출
```

* 클래스와 인스턴스간의 관계 확인하기

```python
lee = Person()
isinstance(lee, Person)
>>>
True
```



## 2. `self` : 인스턴스 객체 자기 자신

* 특별한 상황을 제외하고는 무조건 메서드에서 `self`를 첫번째 인자로 설정
* 메서드는 인스턴스 객체가 함수의 첫번째 인자로 전달되도록 되어있음

```python
lee. greeting()
>>> 홍길동
```

```python
lee.name = '이민지'
lee.greeting()
>>> 이민지
Person.greeting(lee)
>>> 이민지
```

* 만약 greeting에 self를 넣지 않으면 lee.greeting()으로 호출 불가능함(TypeError)

* 클래스 선언부 내부에서도 반드시 self를 통해 데이터 어트리뷰트에 접근해야함.

```python
# 클래스 선언할 때 self가 없음
name = '????????'

class Person:
    name = '홍길동'
    def greeting(self):
        print(f'안녕 {name}')
        
hong = Person()
hong.greeting()
>>>
안녕 ????????
```

```python
# 클래스 선언할 때 self가 있음
name = '????????'

class Person:
    name = '홍길동'
    def greeting(self):
        print(f'안녕 {self.name}')
    
hong = Person()
hong.greeting()
>>>
안녕 홍길동
```



## 3. 클래스 - 인스턴스간의 이름공간

* 클래스를 정의하면 클래스 객체가 생성되고 해당되는 이름 공간이 생성
* 인스턴스를 만들게 되면 인스턴스 객체가 생성되고 해당되는 이름공간이 생성
* 인스턴스의 어트리뷰트가 변경되면, 변경된 데이터를 인스턴스 객체 이름 공간에 저장
* 즉, 인스턴스에서 특정한 어트리뷰트에 접근하게 되면 인스턴스 -> 클래스 순으로 탐색

[참고](https://goo.gl/ZgNaXB) - Person클래스에 iu라는 인스턴스를 생성하고 그 인스턴스의 이름을 지정 전/ 후 이름 프린트



## 4. 생성자 / 소멸자

* 생성자는 인스턴스 객체가 생성될 때 호출되는 함수
* 소멸자는 객체가 소멸되는 과정에서 호출되는 함수
* 생성자는 값을 초기화하는 과정에서 자주 활용됨

```python
def __init__(self):
    print('생성될 때 자동으로 호출되는 메서드입니다.')
    
def __del__(self):
    print('소멸될 때 자동으로 호출되는 메서드입니다.')
```

`__someting__` 처럼 양쪽에 언더스코어(_)가 있는 메서드를 스페셜메서드, 매직 메서드라고 함

* 생성자와 소멸자 만들기

```python
class Person:
    name = '홍길동'
    def __init__(self):
        print('응애')
    def greeting(self):
        print(f'안녕 {self.name}')
    def __del__(self):
        print('으악')
        
p1 = Person()
>>> 응애
# 만약 p1을 또 생성시키면 전에 생성되어있던 p1이 소멸되고 다시 p1이 생성되면서 응애와 으악이 동시에 출력됨
```



* 생성자와 소멸자 역시 메소드이기 때문에 아래처럼 추가적인 인자를 받을 수 있음

```python
def __init__(self, parameter1, parameter2):
    print('생성될 때 자동으로 호출되는 메서드입니다.')
    print(parameter1)

def __init__(self, *args):
    print('생성될 때 자동으로 호출되는 메서드입니다.')

def __init__(self, **kwagrs):
    print('생성될 때 자동으로 호출되는 메서드입니다.')
```



## 5. 클래스 변수 / 인스턴스 변수

```python
class Person:
    population = 0              # 클래스 변수 : 모든 인스턴스가 공유함.
    
    def __init__(self, name):   
        self.name = name        # 인스턴스 변수 : 인스턴스별로 각각 가지는 변수
```



## 6. 정적 메서드 / 클래스 메서드

* 메서드 호출을 인스턴스가 아닌 클래스가 할 수 있도록 구성할 수 있음
* 정적 메소드(static method) : 객체가 전달되지 않은 형태
* 클래스 메소드(class method): 인자로 클래스를 넘겨줌

```python
class Dog:
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    @staticmethod
    def bark():
        print('멍멍')
        
Dog.bark()
>>>
멍멍
```



* static method

  > @staticmethod
  > def methodname():
  >  	codeblock



* class method

  > @classmethod
  > def methodname(cls):
  > 	codeblock



```python
class Dog:
    cnt = 0
    name = '멍뭉이'
    def __init__(self, name, age):
        self.name = name
        self.age = age
        Dog.cnt += 1
    #인스턴스 메소드 doggy.bark() == Dog.bark(doggy)
    
    def bark(self):
        print(f'멍멍, {self.name}')
        
    # 클래스메소드 Dog.count()
    @classmethod
    def count(cls):
        print(f'{cls.cnt}')
        
# @classmethod라고 써두면 iu가 아닌 Person이 넘어감
# 클래스메소드를 정의해두면 호출될 때 클래스 자체의 인스턴스를 넘겨줌
```

```python
# doggy라는 이름을 가진 인스턴스 생성
doggy = Dog('멍멍이', 3)
```

```python
doggy.name
>>>
멍멍이

Dog.name
>>>
멍뭉이
```



### 1) 인스턴스 메소드

1. iu.greeting() == Person.greeting(iu)
2. 첫번째 인자로 iu 오브젝트(인스턴스 오브젝트)가 넘어감
3. self.name형식으로 메소드 내부에서 인스턴스 변수를 가져올 수 있다.



### 2) 클래스 메소드(클래스가 호출) 

1. Person.greeting()하면
2. cls안에는 class인 Person이 들어감



## 7. 연산자 오버라이딩(재정의)

* 파이썬에 기본적으로 정의된 연산자를 직접적으로 정의하여 활용
* 연산자를 내가 원하는 형태로 오버라이딩해서 쓸 수 있음

| 직접 정의 연산자 | 기본 정의 연산자 |
| ---------------- | ---------------- |
| +                 | __add__                 |
| -                 | __sub__                 |
| *                 | __mul__                 |
| <                 | __lt__                 |
| <=                 | __le__                 |
| ==                 | __eq__                 |
| !=                 | __ne__                 |
| >=                 | __ge__                 |
| >                 | __ge__                 |

```python
class Person:
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def __eq__(self, other):
        if self.age == other.age:
            return '둘이 동갑임'
        else:
            return '둘이 동갑이 아님'
        
    def greeting(self):
        print(f'{self.name}입니다. {self.age}살')
```

```python
p1 = Person('a', 24)
p2 = Person('b', 24)
p3 = Person('c', 25)

p1 == p2
>>>
'둘이 동갑임'
p2 == =3
>>>
'둘이 동갑이 아님'
```



