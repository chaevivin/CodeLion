![KakaoTalk_20220514_205821855](https://user-images.githubusercontent.com/83055813/168424688-8f9c13c3-3f07-409d-afc3-7a1c3af4db4b.png)

<br>

# 💻 첫 번째 프로젝트 : 실시간 검색어 확인하기

## 프로젝트 간단 설명

- 크롤링을 이용해서 다음의 실시간 검색어 불러오기

<br>

## 프로젝트 코딩하기

### 1. 크롤링이란?

- 웹사이트를 크롤러가 기어다니면서 데이터 모아줌
- 웹 크롤러 (Web Crawler) : 웹 페이지의 데이터를 모아주는 소프트웨어
- 웹 크롤링 (Web Crawling) : 크롤러를 사용해 웹 페이지의 데이터를 츠츨해 내는 행위

<br>

### 2. 크롤링을 하기 위한 외부 모듈

- 모듈 : 자주 쓰는 함수를 모아놓은 것

```
$ pip install requests
```

- 사용 방법
  1. requests 모듈에서
  2. get 함수를 꺼내서
  3. 요청 명령 -> get 함수가 응답값 return

<br>

- 맨 위에 import requests
- requests.get(url) : 모듈명.함수이름()
  - GET 요청을 보내는 기능
  - return : requests.response

<br>

```python
import requests

url = "https://www.daum.net"
requests.get(url)  # 작성한 서버 주소로 요청을 보냄
print(requests.get(url))  # <Response [200]>
```

- <Response [200]> : 200은 대부분 성공을 의미, 요청이 성공적으로 보내졌고 응답을 받아왔다는 의미

<br>

```python
import requests

url = "https://www.daum.net"
response = requests.get(url)

print(response.text)  # html 코드 받아옴
```

- response.text : 디코드된 컨텐츠값 문자열로 반환
- response.url : 요청 보낸 url
- response.content : response.text와 달리 디코드 되지 않은 컨텐츠값, 미디어 불러올 때 사용
- response.encoding : encoding, 한글깨짐 문제 해결 가능 (예 : UTF-8)
- response.headers : 헤더
- response.json : json을 딕셔너리로 변환 가능
- response.links : 헤더 링크를 파싱한 결과 반환
- response.ok : 요청, 응답코드가 200이면 True
- response.status_code : 상태 코드 반환

<br>

### 3. Beautiful Soup

- Beautiful Soup은 모듈이 아니라 모듈 안에 있는 하나의 기능
- 가지고 온 데이터를 의미있는 데이터로 변경

```python
from bs4 import BeautifulSoup

url = "https://www.daum.net"
response = requests.get(url)

print(BeautifulSoup(response.text, 'html.parser'))
```

- 출력하면 print(response.text)와 출력값이 동일함
- type(response.txt) -> <class 'str'>
  - 문자열
- type(BeautifulSoup(response.text, 'html.parser')) -> <class, 'bs4.BeautifulSoup'>
  - 받아온 하나의 문자열 값을 다 분리해서 저장

<br>

- BeautifulSoup(데이터, 파싱방법)
  - 데이터 : BeautifulSoup 통에 담을 데이터 (html, xml)
  - 파싱(parsing) : 의미있는 데이터로 바꿔주는 것
  - html.parser : 파이썬에 내장되어 있는 html parser

```python
# soup라는 통에 담아줌
soup = BeautifulSoup(response.txt, 'html.parser')

print(soup.title)  # <title>Daum</title>
print(soup.title.string)  # Daum
print(soup.span)  # 맨 위에 있는 span 태그만
print(soup.findAll('span'))  # 모든 span 태그
```

<br>

### 4. Beautiful Soup로 실시산 검색어 받아오기

- html 파일을 보기 쉽게 받아오기

```python
#파일 받아오기
file = open("daum.html","w")
file.write(response.text)
file.close()
```

<br>

- html 파일을 보면서 실시간 검색어들만의 공통점 찾기 (태그나 클래스 중심으로)
  - a 태그
  - 클래스 이름이 'link_favorsch'

```python
# html 문서에서 모든 a 태그 중에서 클래스 이름이 'link_favorsch'인 것 가져오기
results = soup.findAll('a', 'link_favorsch')
```

- 받아온 데이터 text 값만 가져오기

```python
rank = 1  # 순위

for result in results:
    print(rank, "위: ", result.get_text(), "\n")
    rank += 1
```

- 실시간 날짜 가져오기

```python
from datetime import datetime

print(datetime.today().strftime("%y년 %m월 %d일의 실시간 검색어 순위입니다. \n"))  # 오늘 날짜 출력
```

<br>

### 5. 파일로 출력하기

- 파일 열기 : open(파일, 모드)
- 모드 종류
  - r (read) : 파일 읽기
  - w (write) : 파일 쓰기
  - a (append) : 파일에 새로운 내용 추가

```python
# rankressul.txt에 실시간 검색어 쓰기
search_rank_file = open("rankresult.txt". "w")

for result in results:
    search_rank_file.write(str(rank) + "위 : " + result.get_text() + "\n")
```

<br>

## 전체 코드

```python
from bs4 import BeautifulSoup
import requests
from datetime import datetime

url = "http://www.daum.net/"
response = requests.get(url)
soup = BeautifulSoup(response.text, 'html.parser')
rank = 1

results = soup.findAll('a','link_favorsch')

search_rank_file = open("rankresult.txt","a")

print(datetime.today().strftime("%Y년 %m월 %d일의 실시간 검색어 순위입니다.\n"))

for result in results:
    search_rank_file.write(str(rank)+"위:"+result.get_text()+"\n")
    print(rank,"위 : ",result.get_text(),"\n")
    rank += 1
```

<br>
<br>
<br>

# 🌤 두 번째 프로젝트 : 날씨 정보 받아오기

## 프로젝트 간단 설명

- API를 사용하여 날씨 정보를 출력하는 프로그램

<br>

## 프로젝트 코딩하기

### 1. (사전 준비) API key 활성화 하기

- https://home.openweathermap.org/users/sign_up 접속한 후 회원가입
- 로그인 하기
- API key 발급된 것 확인하기

<br>

### 2. API란?

- API (Application Programmin Interface) : 프로그램과 프로그램을 연결해주는 것
- 사용할 API : OpenWeatherMap (세계의 날씨를 모두 볼 수 있는 API)
- Open API : 누구나 사용할 수 있도록 공개한 API
- API key : API를 사용한 사람들의 기록

<br>

### 3. API 링크 만들기

```python
city = "Seoul"
apikey = "################################"
api = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={apikey}"
```

<br>

### 4. 날씨 받아오기

- requests로 요청하기

```python
import requests

...

result = requests.get(api)
```

- python json 모듈 사용하기
  - json (JavaScript Object Notation) : 데이터를 주고 받을 때 사용하는 포맷
  - 딕셔너리 형태

```python
import json

data = json.loads(result.text)  # 받아온 응답값을 json 형태로 변환
```

<br>

### 5. 예쁘게 정리하기

```python
# 날씨
print(data["name"], "의 날씨입니다.")  # Seoul의 날씨입니다.
print("날씨는 ", data["weather"][0]["main"], "입니다.")  # 날씨는 Clouds 입니다.

# 온도
print("현재 온도는 ",data["main"]["temp"],"입니다.")  # 현재 온도는 302.29 입니다.
print("하지만 체감 온도는 ",data["main"]["feels_like"],"입니다.")  # 하지만 체감 온도는 306.81 입니다.
```

- language 파라미터 추가해서 언어 바꾸기

```python
lang = "kr"

api = f"""http://api.openweathermap.org/data/2.5/\
weather?q={city}&appid={apikey}&lang={lang}"""
```

- units 파라미터 추가해서 온도 단위 바꾸기 (화씨 -> 섭씨)

```python
api = f"""http://api.openweathermap.org/data/2.5/\
weather?q={city}&appid={apikey}&lang={lang}&units=metric"""
```

<br>

## 전체 코드

```python
import requests
import json

city = "Seoul"
apikey = "################################"
lang = "kr"
# units - metric
api = f"""http://api.openweathermap.org/data/2.5/\
weather?q={city}&appid={apikey}&lang={lang}&units=metric"""

result = requests.get(api)
# print(result.text)

data = json.loads(result.text)

# 지역 : name
print(data["name"],"의 날씨입니다.")
# 자세한 날씨 : weather - description
print("날씨는 ",data["weather"][0]["description"],"입니다.")
# 현재 온도 : main - temp
print("현재 온도는 ",data["main"]["temp"],"입니다.")
# 체감 온도 : main - feels_like
print("하지만 체감 온도는 ",data["main"]["feels_like"],"입니다.")
# 최저 기온 : main - temp_min
print("최저 기온은 ",data["main"]["temp_min"],"입니다.")
# 최고 기온 : main - temp_max
print("최고 기온은 ",data["main"]["temp_max"],"입니다.")
# 습도 : main - humidity
print("습도는 ",data["main"]["humidity"],"입니다.")
# 기압 : main - pressure
print("기압은 ",data["main"]["pressure"],"입니다.")
# 풍향 : wind - deg
print("풍향은 ",data["wind"]["deg"],"입니다.")
# 풍속 : wind - speed
print("풍속은 ",data["wind"]["speed"],"입니다.")
```

<br>
<br>
<br>

# 📝 세 번째 프로젝트 : 번역기 프로그램

## 프로그램 간단 설명

- 한글 -> 영어로 번역해주는 프로그램

<br>

## 프로그램 코딩하기

### 1. Googletrans란?

- 언어 감지 및 번역 기능을 가진 라이브러리

```python
from googletrans import Translator
```

<br>

### 2. 언어 감지하기

- 번역기를 만든다.

```python
translator = Translator()
```

- 언어 감지를 원하는 문장을 설정한다.

```python
sentence = "안녕하세요. 코드라이언입니다."
```

- 언어를 감지한다.

```python
detected = translator.detect(sentence)
print(detected)  # Detected(lang=ko, confidence=1.0) -> confidence : 신뢰성

# 언어만
print(detected.lang)  # ko
```

- 사용자에게 집적 입력받은 문장의 언어 감지

```python
sentence = input("언어를 감지할 문장을 입력해주세요 : ")
detected = translator.detect(sentence)

print(detected.lang)
```

<br>

### 3. 문장 번역하기

- 번역기를 만든다.
- 번역을 원하는 문장을 설정한다.
- 번역을 원하는 언어를 설정한다.
- 번역한다.
- translate(번역할 문장, 번역할 언어, 텍스트의 언어(생략가능))

```python
result = translator.translate(sentence, 'en')
print(result)  # Translated(src=ko, dest=en, text=hello, this is codelion., pronunciation=None, extra_data="{'transla...}")
```

```python
print(detected.lang, ":", sentence)  # ko: 안녕하세요, 코드라이언입니다.
print(result.dest, ":", result.text)  # en: Hello, this is codelion.
```

<br>

## 전체 코드

```python
from googletrans import Translator

translator = Translator()

# sentence = "안녕하세요 코드라이언입니다."
sentence = input("번역을 원하는 문장을 입력해주세요 : ")
dest = input("어떤 언어로 번역을 원하시나요?")

result = translator.translate(sentence,dest)
detected = translator.detect(sentence)

print("===========출 력 결 과===========")
print(detected.lang,":",sentence)
print(result.dest,":",result.text)
print("=================================")
```

<br>
<br>
<br>

# 4. ✉ 네 번째 프로젝트 : 메일 보내기

## 프로젝트 간단 설명

- 메일이 자동으로 전송되는 프로그램

<br>

## 프로젝트 코딩하기

### 1. 사전 준비

- Gmail IMAP 사용 설정하기 : IMPA 사용 허가로 바꾸기
- 메일 계정의 외부 접속에 대한 보안 설정 : 계정 관리 > 보안 > 보안 수준이 낮은 앱의 엑세스 허용

<br>

### 2. SMTP (Simple Mail Transfer Protocol)

- 클라이언트(다른 서버)에서 이메일 서버로 메일을 보낼 때 사용
- IMAP : 이메일 서버에서 클라이언트로 이메일 보낼 때 사용
- SMTP 서버(이메일 서버)를 이용해서 우리가 원하는 곳으로 메일을 보낼 수 있다.
- 순서

  - SMTP 메일 서버를 연결한다.

  ```python
  import smtplib

  SMTP_SERVER = "smtp.gmail.com"
  SMTP_PORT = 465

  # 서버에 연결
  smtp = smtplib.SMTP_SSL(SMTP_SERVER, SMTP_PORT)
  ```

  - SMTP 메일 서버에 로그인한다.

  ```python
  smtp.login("###@gmail.com", "#######")  # 이메일, 구글 비밀번호
  ```

  - SMTP 메일 서버로 메일을 보낸다.

  ```python
  smtp.send_message()  # 메일 내용
  ```

<br>

### 3. MIME

- SMTP에 메일을 보내기 전 메일 내용을 MIME 형태로 바꿔야 함
- email.message 모듈 : .EmailMessage 기능 사용해서 MIME 형태로 바꾼다.
- 순서

  - 이메일을 만든다.

  ```python
  from email.message import EmailMessage

  message = EmailMessage()
  ```

  - 이메일에 내용을 담는다.

  ```python
  # CONTENT
  message.set_content("코드라이언")  # 메시지 내용
  ```

  - 발신자, 수신자를 설정한다.

  ```python
  # HEADER
  message["Subject"] = "제목"
  message["From"] = "###@gmail.com"  # 발신자
  message["To"] = "***@gmail.com"  # 수신자
  ```

<br>

### 4. 메일 전송하기

```python
smtp.send_message(message)
```

<br>

### 5. 메일에 사진 첨부하기

- 이미지 파일 읽어오기
  - rb : read binary
  - wb : write binary
  - ab : append binary

```python
# close문 없이 읽고 쓸 수 있음
with open("codelion.png", "rb") as image:
    image_file = image.read()
```

- add_attachment() : text가 아닌 다른 파일들을 첨부할 때 사용 (MIME MIXED 타입)
  - image : 첨부할 내용
  - maintype : 첨부할 내용의 유형 (img, vid , ...)
  - subtype : 확장자 (png, mp4, ...)

```python
message.add_attachment(image_file, maintype='image', subtype=image_type)  # subtype은 밑에 참고
```

- image의 확장자가 계속 변할 때 사용할 수 있는 모듈

```python
import imghdr

image_type = imgher.what('codelion', image_file)  # 어떤 확장자인지 파악
```

<br>

### 6. 유효성 검사하기

- 보내고자 하는 이메일 주소가 유효한지 검사 / 판단
- 정규표현식 : 문자열에서 나타나는 일정한 패턴 파악 후 대응
  - 이메일에서만 나타나는 일정한 패턴을 조건으로 주고 이 조건의 문자열이 적합한지 판단

<br>

📧 이메일의 정규 표현식

```
^[a-zA-Z0-9.+_-]+@[a-zA-Z0-9]+\.[a-zA-Z]{2,3}$
```

- ^ : 시작, $ : 끝
- 첫 번째 [ ] : a부터 z까지, A부터 Z까지, 0부터 9까지, ., +, \_, - 가 1회 이상 반복된다.
- @ : 그 뒤에 @가 붙는다.
- a부터 z까지, A부터 Z까지, 0부터 9까지가 1회 이상 반복된다.
- \. : 그 뒤에 .이 붙는다.
- a부터 z까지, A부터 Z까지가 최소 2회, 최대 3번 반복된다.

<br>

- 정규표현식 사용하기 위해서는 re 모듈 import

```python
import re

reg = "^[a-zA-Z0-9.+_-]+@[a-zA-Z0-9]+\.[a-zA-Z]{2,3}$"
print(re.match(reg, "codelion.examplegmailcom"))  # None
print(re.match(reg, "codelion.example@gmail.com"))
```

- 유효성 검사 후 메일 보내기
  - 유효하다면 메일 보내기
  - 유효하지 않다면 메일 보내지 않기

```python
def sendEmail(addr):
    reg = "^[a-zA-Z0-9.+_-]+@[a-zA-Z0-9]+\.[a-zA-Z]{2,3}$"
    if bool(re.match(reg, addr)):
        smtp.send_message(message)
        print("정상적으로 메일이 발송되었습니다.")
    else:
        print("유효한 이메일 주소가 아닙니다.")

sendEmail("###@gmail.com")
```

<br>

## 전체 코드

```python
import smtplib
from email.message import EmailMessage
import imghdr
import re

SMTP_SERVER = "smtp.gmail.com"
SMTP_PORT = 465

def sendEmail(addr):
    reg = "^[a-zA-Z0-9.+_-]+@[a-zA-Z0-9]+\.[a-zA-Z]{2,3}$"
    if bool(re.match(reg,addr)):
        smtp.send_message(message)
        print("정상적으로 메일이 발송되었습니다.")
    else:
        print("유효한 이메일 주소가 아닙니다.")

message = EmailMessage()
message.set_content("코드라이언 수업중입니다.")

message["Subject"] = "이것은 제목입니다."
message["From"] = "###@gmail.com"
message["To"] = "###@gmail.com"

with open("codelion.png","rb") as image:
    image_file = image.read()

image_type = imghdr.what('codelion',image_file)
message.add_attachment(image_file,maintype='image',subtype=image_type)

smtp = smtplib.SMTP_SSL(SMTP_SERVER,SMTP_PORT)
smtp.login("###@gmail.com","######")
sendEmail("###@gmailcom")
smtp.quit()
```
