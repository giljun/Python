# Python Day_2

## 기초 문법

- complex(복소수)

  - 복소수는 허수부를 j로 표현한다.

    ```python
    a = 3+2j
    b = complex(3, -4)
    
    # a = 3+2j, b = 3-4j
    # type of a : complex
    ```

- Bool

  - 파이썬에는 True와 False로 이뤄진 bool 타입이 있다.
  - 비교/논리 연산을 수행 등에서 활용된다.
  - 다음은 False로 변환됩니다.
    - 0, 0.0, (), [], {}, '', None

- None

  - 파이썬에서는 값이 없음을 표현하기 위해 None 타입이 존재

    ```python
    a = None
    print(type(a))
    
    # a = None, type of a : Nonetype
    ```



### 문자형(String)

- 기본 활용법

- 문자열은 Single quotes(')나 Double quotes(")을 활용하여 표현 가능하다.

- 단, 문자열을 묶을 때 동일한 문장부호를 활용해야하며, PEP-8에서는 하나의 문장부호를 선택하여 유지하도록 하고 있습니다.(Pick a rule and Stick to it)

- 여러줄에 걸쳐있는 문장은 다음과 같이 표현 가능합니다.

- PEP-8에 따르면 이 경우에는 반드시 """를 사용하도록 되어 있습니다.

- 이스케이프 문자열

  - 문자열을 활용하는 경우 특수문자 혹은 조작을 하기 위하여 사용되는 것으로 \ 를 활용하여 이를 구분한다.

  - 깜짝 퀴즈

    - 다음의 문장을 출력해보세요

      - """ 사용 금지 

      - print 여러번 사용 금지

        ```python
        print("\"파일은 C:\\Windows\\Users\\내문서\\Python에 저장이 되어있습니다.\"\n나는 생각했다.\'cd를 써서 git bash로 들어가봐야지\'")
        ```

- %, str-format, f-string 관련

  ```python
  # %-formatting
  # 코드가 더러워진다는 단점이 존재
  name = 'hello %s' % 'giljun'
  # str.format
  # 파이썬3 이후부터 새로운 포맷팅을 제시한다.
  # % operator를 지원하지만 공식문서에서는 권장하지 않는다.
  # name2 = 'hello {}'.format('bob')
  name2 = 'hello {1}. count:{0}'.format(10, 'jun')
  
  # f-string은 파이썬 3.6 이상 버전에서만 지원하는 문법입니다.
  # str.format이 % operator에 비해 강력하고 사용하기 쉽지만 f-string은 더욱더 간편해졌습니다.
  
  name = 'Bob'
  name3 = f'hello {name}'
  
  # 정수끼리의 산술 연산도 지원한다.
  a = 2
  b = 3
  name3 = f'sum: {a+b}'
  
  # f=string 선언을 먼저 한 후, 변수를 나중에 선언하는 형식 또한 가능합니다.
  name3 = f'Hi {name}'
  name = 'Bob'
  
  # f-string에서는 형식을 지정할 수 있으며,
  # 다양한 형식을 활용하기 위해서 datetime 모듈로 오늘을 표현해봅시다.
  # 예쁘게 출력해봅시다.
  date = datetime.datetime.now()
  now = f'{date:%Y-%m-%d} is on a {date:%A}'
  print(now)
  ```

  - 속도는 f-string이 가장 빠른 것으로 확인할 수 있습니다.

- 

