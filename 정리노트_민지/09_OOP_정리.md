# OOP_정리

* 인스턴스 메소드 : 첫번째 인자로 인스턴스 객체를 전달함(self)
* 클래스 메소드 : 첫번째 인자로 클래스 객체를 전달함(cls)
* 정적 메소드 : 인자로 어떠한 객체도 전달하지 않음

```python
class Person:
    title = '사람입니다.'
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def instance_method(self):
        print(self)
        print(f'{self.name}')
        
    def greeting(self):
        print(self)
        print('안녕')
        
    @staticmethod
    def static_method(nothing):
        print(nothing)
        
    @classmethod
    def class_method(cls):
        print(cls)
        print(f'{cls.title}')
```

```python
# 클래스 Person의 네임스페이스 확인 가능
Person.__dict__
>>>
mappingproxy({'__module__': '__main__',
              'title': '사람입니다',
              '__init__': <function __main__.Person.__init__(self, name, age)>,
              'instance_method': <function __main__.Person.instance_method(self)>,
              'greeting': <function __main__.Person.greeting(self)>,
              'static_method': <staticmethod at 0x52b5080>,
              'class_method': <classmethod at 0x52b50b8>,
              '__dict__': <attribute '__dict__' of 'Person' objects>,
              '__weakref__': <attribute '__weakref__' of 'Person' objects>,
              '__doc__': None})
```

```python
# 인스턴스 p1의 네임스페이스 확인
p1.__dict__
>>>
{'name': '이민지', 'age': 25}
# title은 인스턴스에는 없고 클래스에 있으니까 따로 확인해야함
p1.title
>>>
사람입니다.
```



* 인스턴스 메소드는 인스턴스 자기 자신(self)를 인자로 넘김
* 괄호 안이 비어있어도 자동으로 self자리에 들어감(위에서 self로 지정해줬기 때문에)

```python
p1.instance_method()
>>>
<__main__.Person object at 0x00000000052BF358>
이민지
```



* 클래스 메소드는 클래스 객체(cls)를 인자로 넘김
* 괄호 안이 비어있어도 자동으로 cls자리에 들어감(위에서 self로 지정해줬기 때문에)

```python
Person.class_method()
>>>
<class '__main__.Person'>
사람입니다
```



* 정적 메소드는 자동으로 값을 넘겨주지 않기 때문에 직접 값을 넣어줘야 함

```python
# 값을 넣어주지 않음
Person.static_method()
>>>
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-10-7342c78d1eb0> in <module>
----> 1 Person.static_method()

TypeError: static_method() missing 1 required positional argument: 'nothing'
```

```python
# 값을 넣어줌
p1.instance_method('hi')
>>>
hi
```

