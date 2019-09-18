# OOP_intro

* 객체 지향 프로그래밍

* `클래스` : 어떠한 형태를 추상화하는 것. 같은 종류의 집단에 속하는 속성(attribute)와 행위(behavior)을 정의한 것

* `인스턴스` : 클래스의 인스턴스(실제로 메모리상에 할당된 것)

* `메서드` : 클래스로부터 생성된 객체를 사용하는 방법, 객체에 명령을 내리는 것

  > 클래스를 선언하면서 어떠한 형태를 추상화, 모습을 그린 후
  >
  > 인스턴스를 통해 하나씩 실체화 한 것
  >
  > 실체화 될 때마다 정보를 입력해놓고 데이터가 어떤 행동을 직접적으로 할 수 있고 정보를 가지고 있음

* 타입을 많이 찍어봐야 하는 이유 : 클래스(str, list, dict 등)마다 할 수 있는 행동이 다르고 정보가 다르게 저장되어 있음



# 클래스 및 인스턴스

## 1. 클래스 객체

> class ClassName:

* 선언과 동시에 클래스 객체가 생성
* 선언된 공간은 지역 스코프로 사용
* 정의된 어트리뷰트 중 변수는 멤버 변수라고 부름
* 정의된 함수 `def`는 메서드라고 부름
* 선언할 때 self는 반드시 써야 함
* 클래스 이름은 대문자로 시작하게 짓는 것이 관례
* 사람

```python
#클래스 이름 : Person
# 메서드 이름 : greeting
class Person:
    name = '이민지'
    def greeting(self):
        print(f'hello, {self.name}')
```



## 2. 인스턴스 객체

* 인스턴스 객체는 `ClassName()`을 호출하면서 선언
* 인스턴스 객체와 클래스 객체는 서로 다른 이름 공간을 가짐
* 인스턴스 -> 클래스 -> 전역 순으로 탐색함
* 사람 중 민지, 민경 처럼 개개인

```python
# Person 클래스의 인스턴스 생성
iu = Person()
```

```python
# 인사하는 메서드 호출
iu.greeting()
>>>
hello, 이민지
# 아직 iu인스턴스에 이름을 설정하지 않아서 클래스에서 선언된 이름이 나옴
```

```python
# iu 인스턴스의 이름 변경 후 인사하는 메서드 호출
iu.name = '아이유'
iu.greeting()
>>>
hello, 아이유
```



* 인스턴스의 타입과 클래스가 같은지 확인

```python
a = 3
type(a) == int
# 인스턴스 a의 타입이 클래스 int와 같은가?
```

```python
type(iu) == Person
>>>
True
```

* 다른 방법으로도 확인할 수 있음

```python
isinstance(a, int)
isinstance(iu, Person)
```



* 파이썬 출력의 비빌 : repr, str

```python
셀프 : 호출될 때 인자로 념겨주는 게 자기 자신임
    인스턴스 자기 자신을 뜻 함
```

```python
class Person:
    # 클래스의 name
    name = '이민지'
    def greeting(self):
        # self는 호출할 때 자기자신(인스턴스)을 인자로 넘기는 것
        print(f'hello, {self.name}')
    def __str__(self):
        # str : 사용자들을 위한 것. 프린트했을 때 호출됨
        return f'사람 : {self.name}'
    def __repr__(self):
        # repr : idle, jupyter notebook, pytho ==> 개발할 때 편하게 보여주는 것
        return f'사람 \n : {self.name}'
    
    # str이 없으면 repr호출
    # repr은 없어도 str을 호출하지 않음
```

* str 확인

```python
iu = Person()
iu.name = '아이유'
print(iu)
>>>
사람 : 아이유
```

* repr 확인

```python
iu
>>>
사람
 : 아이유
```



