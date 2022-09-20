# 코딩 스타일 규칙

## 스페이스바 또는 탭

스페이스바를 선호 한다. 그리고 파이썬에서는 탭과 스페이스바의 혼용 사용을 금지 한다.
파일에서 클래스 또는 메서드 사이에서는 빈 두 줄로 구분 한다.

## Import

### import는 일반적으로 별도의 라인에 있어야합니다.

```python
# 👍 좋음
import os
import sys

# ❌ 나쁨
import sys, os
```

아래의 경우에는 괜찮다.

```python
from subprocess import Popen, PIPE
```

### import는 위치

 항상 파일의 위 쪽에 있어야 한다. 주석과 독스트링, 그리고 모듈 전역 및 상수 앞에 있습니다.

import는 다음 순서로 그룹화되어야 합니다.

- 표준 라이브러리 import.
- 연관 된 서드 파티 import
- 로컬 애플리케이션/라이브러리 특정 import.

## Naming convention

### 변수

* 소문자와 밑줄로 구성한다. - 스네이크케이스([snake_case](https://en.wikipedia.org/wiki/Snake_case))

```python
# 👍 좋음
empty_value = 10

# ❌ 나쁨
emptyValue = 10
```

### 상수

* 대문자와 밑줄로 구성한다. -스크리밍스네이크케이스([SCREAMING_SNAKE_CASE](https://en.wikipedia.org/wiki/SCREAMING_SNAKE_CASE))

```python
# 👍 좋음
START_INDEX = 10

# ❌ 나쁨
start_index = 10
Start_Index = 10
```

### 클래스명

- 파스칼케이스([PascalCase](https://pl.wikipedia.org/wiki/PascalCase))를 사용한다.
  - 첫자를 대문자, 문자마다 첫 문자를 대문자로 써서 연결한다. 밑줄은 사용하지 않는다.
- 예외(Exception)은 실제로 에러인 경우, `Error`를 붙인다.

```python
# 👍 좋음
class DataManager:

# ❌ 나쁨
class Data_manager:
```

#### 메서드명

* 스네이크케이스([snake_case](https://en.wikipedia.org/wiki/Snake_case))를 사용한다.

* 인스턴스 메소드의 첫번째 인자는 언제나 `self`이다.

* 클래스 메소드의 첫번째 인자는 언제나 `cls`이다.

* 메소드명은 함수명과 같으나 보호(protected)와 비공개(private)이면 앞에 _(밑줄)을 붙여준다.
  
  * protected : 밑줄 한개 => _leading_underscore
  
  * private : 밑줄 두개=> ___leading_underscore

* 서브 클래스(sub-class)의 이름 충돌을 막기 위해서는 밑줄 2개를 앞에 붙인다.
  
  ```python
  # 👍 좋음
  def add_node(self, num):
  
  # ❌ 나쁨
  
  def addNode(self, num):
  def AddNode(self, num):
  ```

### _(밑줄) 사용 법

* 변수명의 _(밑줄)은 다음과 같은 의미
  * _single_leading_underscore: 내부적으로 사용되는 변수를 일컫습니다.
  * single_trailing_underscore_: 파이썬 기본 키워드와 충돌을 피하려고 사용합니다.
  * \_\_double_leading_underscore: 클래스 속성으로 사용되면 그 이름을 변경합니다.
     (ex. FooBar에 정의된 \_\_boo는 _FooBar\_\_boo로 바뀝니다.)
  * \_\_double_leading_and_trailing_underscore__: 마술(magic)을 부리는 용도로 사용되거나 사용자가 조정할 수 있는 네임스페이스 안의 속성을 뜻합니다. 이런 이름을 새로 만들지 마시고 오직 문서대로만 사용하세요.

### 파일명

* 파일명은 스네이크케이이(snake_case)에 따른다.
* 클래스가 하나만 들어 있는 경우 클래스의 이름과 같은 파스칼케이스(PascalCase)를 사용한다.

## 코딩 규칙

* [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/)
* [PEP 8 파이썬 코딩 스타일](http://pythonstudy.xyz/python/article/511-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%BD%94%EB%94%A9-%EC%8A%A4%ED%83%80%EC%9D%BC)
* [Python PEP 8](https://b.luavis.kr/python/python-convention)
* [파이썬 코딩 컨벤션](https://spoqa.github.io/2012/08/03/about-python-coding-convention.html)
