# 파이썬 설정

## 파이썬 설치 하기

`pyenv`를 설치하고 python을 설치 하자..
이것도 버전 관리가 필요 함..

* https://pyenv-win.github.io/pyenv-win/

초코로 아래와 같이 설치하는게 가장 간단.

```
choco install pyenv-win
pyenv install --list
pyenv install [version]
```

현재 프로젝트는 `3.9.6`에서 작업을 시작 했음.



-------

# peotry

## poetry(패키지 관리자) 설치

### osx / linux / bashonwindows install instructions

```
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -
```

### pip로 설치

```
pip install --user poetry
```

설치가 되긴 하지만 추천하지 않다. 이유는  가상 개발 환경에도 poetry를 설치해 줘야 하는 불편함이 있다.

#### Powershell

```
(Invoke-WebRequest -Uri https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py -UseBasicParsing).Content | python -
```

설치 이후 `PATH` 환경 변수에 아래 내용을 추가 해 준다.

```
%USERPROFILE%\.poetry\bin
```

### peotry 설정하기

그냥 peotry를 사용하게 되면 user 폴더에 .venv 파일이 생성되어서.. vscode에서는 연결해서 사용하기 어렵다. 그래서 아래와 .venv 파일의 경우를 프로젝트 경로에 생성 되도록 해 준다.

```
poetry config virtualenvs.in-project true
poetry config virtualenvs.path "./.venv"
```

## 파이썬 가상 환경 만들어 주기

### peotry로 만들기

```
peotry install
.venv/Scripts/activate
```

`peotry`를 해 주면.. `.venv` 폴더를 만들고 여기에 패키지를 설치해 준다.

# 실행하기

> uvicorn main:app --reload



---

# poetry 사용법

## init

init 커맨드는 pyproject.toml 파일을 인터렉티브 하게 만들 수 있도록 도와준다.

```bash
poetry init
```

## install

install 커맨드는 현재 프로젝트의 pyproject.toml 파일을 읽어서 의존성 패키지를 설치해준다. poetry.lock 이 없으면 만들어 주고 있으면 해당파일을 사용하게 된다.

```bash
# 의존성 설치
poetry install
# 개발환경의 의존성은 빼고 설치
poetry install --no-dev
# -E 또는 --extras 로 추가 의존성을 설정가능
poetry install --extras "mysql redis"
poerty install -E mysql -E redis
```

## 패키지 추가하기

```bash
poetry add django
# 개발환경에서 필요한 패키지 설치
poetry add pytest factory-boy --dev
# 버전을 지정가능
poetry add django@^3.0.0
poetry add "django=3.0.0"
# 최신버전을 설치
poetry add django@latest
# 깃 저장소에 있는 패키지 설치
poetry add git+https://github.com/django/django.git
# 깃 저장소의 패키지에서 브랜치를 지정
poetry add git+https://github.com/django/django.git#stable/2.2.x
# 로컬에 디렉토리의 파일로 설치하기
poetry add ./my-package/
poetry add ./my-package/dist/my-package-0.1.0.tar.gz
poetry add ./my-package/dist/my-package-0.1.0.whl
```

## 패키지 업데이트

의존성 패키지의 버전을 업데이트하고 poetry.lock 파일을 업데이트 한다.

```bash
# 패키지 업데이트
poerty update
# 하나씩 지정해서 업데이트도 가능
poetry update requests toml
# 업데이트는 하지 않고 poetry.lock 만 업데이트
poerty update --lock
```

## 패키지 지우기

```bash
poetry remove flask
# 개발환경 패키지 삭제
poetry remove pytest
```

## 설치된 패키지 조회

```bash
# 설치된 모든 패키지를 보여준다.
poetry show

# 개발환경용 제외하고 보여준다.
poetry show --no-dev

# 특정패키지를 지정하면 상세내용을 보여줍니다.
poetry show django

# 최신 버전을 보여준다.
poetry show --latest (-l)

# 업데이트를 해야하는 패키지들을 보여준다.
poetry show --outdate (-o)

# 의존성 트리를 보여준다.
poetry show --tree
```

## 

# 참고

* [Poetry를 사용하여 가상환경 만들기](https://velog.io/@hj8853/Poetry%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-%EA%B0%80%EC%83%81%ED%99%98%EA%B2%BD-%EB%A7%8C%EB%93%A4%EA%B8%B0)
* [파이썬 패키지 관리툴 poetry 소개](https://blog.gyus.me/2020/introduce-poetry/)
* [파이썬 의존성 관리자 Poetry 사용기](https://spoqa.github.io/2019/08/09/brand-new-python-dependency-manager-poetry.html)
* [파이썬 환경 구축기 - pyenv + poetry](https://dailyheumsi.tistory.com/244)