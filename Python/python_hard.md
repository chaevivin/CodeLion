![KakaoTalk_20220514_205821855](https://user-images.githubusercontent.com/83055813/168424688-8f9c13c3-3f07-409d-afc3-7a1c3af4db4b.png)

<br>

# ๐ป ์ฒซ ๋ฒ์งธ ํ๋ก์ ํธ : ์ค์๊ฐ ๊ฒ์์ด ํ์ธํ๊ธฐ

## ํ๋ก์ ํธ ๊ฐ๋จ ์ค๋ช

- ํฌ๋กค๋ง์ ์ด์ฉํด์ ๋ค์์ ์ค์๊ฐ ๊ฒ์์ด ๋ถ๋ฌ์ค๊ธฐ

<br>

## ํ๋ก์ ํธ ์ฝ๋ฉํ๊ธฐ

### 1. ํฌ๋กค๋ง์ด๋?

- ์น์ฌ์ดํธ๋ฅผ ํฌ๋กค๋ฌ๊ฐ ๊ธฐ์ด๋ค๋๋ฉด์ ๋ฐ์ดํฐ ๋ชจ์์ค
- ์น ํฌ๋กค๋ฌ (Web Crawler) : ์น ํ์ด์ง์ ๋ฐ์ดํฐ๋ฅผ ๋ชจ์์ฃผ๋ ์ํํธ์จ์ด
- ์น ํฌ๋กค๋ง (Web Crawling) : ํฌ๋กค๋ฌ๋ฅผ ์ฌ์ฉํด ์น ํ์ด์ง์ ๋ฐ์ดํฐ๋ฅผ ์ธ ์ธจํด ๋ด๋ ํ์

<br>

### 2. ํฌ๋กค๋ง์ ํ๊ธฐ ์ํ ์ธ๋ถ ๋ชจ๋

- ๋ชจ๋ : ์์ฃผ ์ฐ๋ ํจ์๋ฅผ ๋ชจ์๋์ ๊ฒ

```
$ pip install requests
```

- ์ฌ์ฉ ๋ฐฉ๋ฒ
  1. requests ๋ชจ๋์์
  2. get ํจ์๋ฅผ ๊บผ๋ด์
  3. ์์ฒญ ๋ช๋ น -> get ํจ์๊ฐ ์๋ต๊ฐ return

<br>

- ๋งจ ์์ import requests
- requests.get(url) : ๋ชจ๋๋ช.ํจ์์ด๋ฆ()
  - GET ์์ฒญ์ ๋ณด๋ด๋ ๊ธฐ๋ฅ
  - return : requests.response

<br>

```python
import requests

url = "https://www.daum.net"
requests.get(url)  # ์์ฑํ ์๋ฒ ์ฃผ์๋ก ์์ฒญ์ ๋ณด๋
print(requests.get(url))  # <Response [200]>
```

- <Response [200]> : 200์ ๋๋ถ๋ถ ์ฑ๊ณต์ ์๋ฏธ, ์์ฒญ์ด ์ฑ๊ณต์ ์ผ๋ก ๋ณด๋ด์ก๊ณ  ์๋ต์ ๋ฐ์์๋ค๋ ์๋ฏธ

<br>

```python
import requests

url = "https://www.daum.net"
response = requests.get(url)

print(response.text)  # html ์ฝ๋ ๋ฐ์์ด
```

- response.text : ๋์ฝ๋๋ ์ปจํ์ธ ๊ฐ ๋ฌธ์์ด๋ก ๋ฐํ
- response.url : ์์ฒญ ๋ณด๋ธ url
- response.content : response.text์ ๋ฌ๋ฆฌ ๋์ฝ๋ ๋์ง ์์ ์ปจํ์ธ ๊ฐ, ๋ฏธ๋์ด ๋ถ๋ฌ์ฌ ๋ ์ฌ์ฉ
- response.encoding : encoding, ํ๊ธ๊นจ์ง ๋ฌธ์  ํด๊ฒฐ ๊ฐ๋ฅ (์ : UTF-8)
- response.headers : ํค๋
- response.json : json์ ๋์๋๋ฆฌ๋ก ๋ณํ ๊ฐ๋ฅ
- response.links : ํค๋ ๋งํฌ๋ฅผ ํ์ฑํ ๊ฒฐ๊ณผ ๋ฐํ
- response.ok : ์์ฒญ, ์๋ต์ฝ๋๊ฐ 200์ด๋ฉด True
- response.status_code : ์ํ ์ฝ๋ ๋ฐํ

<br>

### 3. Beautiful Soup

- Beautiful Soup์ ๋ชจ๋์ด ์๋๋ผ ๋ชจ๋ ์์ ์๋ ํ๋์ ๊ธฐ๋ฅ
- ๊ฐ์ง๊ณ  ์จ ๋ฐ์ดํฐ๋ฅผ ์๋ฏธ์๋ ๋ฐ์ดํฐ๋ก ๋ณ๊ฒฝ

```python
from bs4 import BeautifulSoup

url = "https://www.daum.net"
response = requests.get(url)

print(BeautifulSoup(response.text, 'html.parser'))
```

- ์ถ๋ ฅํ๋ฉด print(response.text)์ ์ถ๋ ฅ๊ฐ์ด ๋์ผํจ
- type(response.txt) -> <class 'str'>
  - ๋ฌธ์์ด
- type(BeautifulSoup(response.text, 'html.parser')) -> <class, 'bs4.BeautifulSoup'>
  - ๋ฐ์์จ ํ๋์ ๋ฌธ์์ด ๊ฐ์ ๋ค ๋ถ๋ฆฌํด์ ์ ์ฅ

<br>

- BeautifulSoup(๋ฐ์ดํฐ, ํ์ฑ๋ฐฉ๋ฒ)
  - ๋ฐ์ดํฐ : BeautifulSoup ํต์ ๋ด์ ๋ฐ์ดํฐ (html, xml)
  - ํ์ฑ(parsing) : ์๋ฏธ์๋ ๋ฐ์ดํฐ๋ก ๋ฐ๊ฟ์ฃผ๋ ๊ฒ
  - html.parser : ํ์ด์ฌ์ ๋ด์ฅ๋์ด ์๋ html parser

```python
# soup๋ผ๋ ํต์ ๋ด์์ค
soup = BeautifulSoup(response.txt, 'html.parser')

print(soup.title)  # <title>Daum</title>
print(soup.title.string)  # Daum
print(soup.span)  # ๋งจ ์์ ์๋ span ํ๊ทธ๋ง
print(soup.findAll('span'))  # ๋ชจ๋  span ํ๊ทธ
```

<br>

### 4. Beautiful Soup๋ก ์ค์์ฐ ๊ฒ์์ด ๋ฐ์์ค๊ธฐ

- html ํ์ผ์ ๋ณด๊ธฐ ์ฝ๊ฒ ๋ฐ์์ค๊ธฐ

```python
#ํ์ผ ๋ฐ์์ค๊ธฐ
file = open("daum.html","w")
file.write(response.text)
file.close()
```

<br>

- html ํ์ผ์ ๋ณด๋ฉด์ ์ค์๊ฐ ๊ฒ์์ด๋ค๋ง์ ๊ณตํต์  ์ฐพ๊ธฐ (ํ๊ทธ๋ ํด๋์ค ์ค์ฌ์ผ๋ก)
  - a ํ๊ทธ
  - ํด๋์ค ์ด๋ฆ์ด 'link_favorsch'

```python
# html ๋ฌธ์์์ ๋ชจ๋  a ํ๊ทธ ์ค์์ ํด๋์ค ์ด๋ฆ์ด 'link_favorsch'์ธ ๊ฒ ๊ฐ์ ธ์ค๊ธฐ
results = soup.findAll('a', 'link_favorsch')
```

- ๋ฐ์์จ ๋ฐ์ดํฐ text ๊ฐ๋ง ๊ฐ์ ธ์ค๊ธฐ

```python
rank = 1  # ์์

for result in results:
    print(rank, "์: ", result.get_text(), "\n")
    rank += 1
```

- ์ค์๊ฐ ๋ ์ง ๊ฐ์ ธ์ค๊ธฐ

```python
from datetime import datetime

print(datetime.today().strftime("%y๋ %m์ %d์ผ์ ์ค์๊ฐ ๊ฒ์์ด ์์์๋๋ค. \n"))  # ์ค๋ ๋ ์ง ์ถ๋ ฅ
```

<br>

### 5. ํ์ผ๋ก ์ถ๋ ฅํ๊ธฐ

- ํ์ผ ์ด๊ธฐ : open(ํ์ผ, ๋ชจ๋)
- ๋ชจ๋ ์ข๋ฅ
  - r (read) : ํ์ผ ์ฝ๊ธฐ
  - w (write) : ํ์ผ ์ฐ๊ธฐ
  - a (append) : ํ์ผ์ ์๋ก์ด ๋ด์ฉ ์ถ๊ฐ

```python
# rankressul.txt์ ์ค์๊ฐ ๊ฒ์์ด ์ฐ๊ธฐ
search_rank_file = open("rankresult.txt". "w")

for result in results:
    search_rank_file.write(str(rank) + "์ : " + result.get_text() + "\n")
```

<br>

## ์ ์ฒด ์ฝ๋

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

print(datetime.today().strftime("%Y๋ %m์ %d์ผ์ ์ค์๊ฐ ๊ฒ์์ด ์์์๋๋ค.\n"))

for result in results:
    search_rank_file.write(str(rank)+"์:"+result.get_text()+"\n")
    print(rank,"์ : ",result.get_text(),"\n")
    rank += 1
```

<br>
<br>
<br>

# ๐ค ๋ ๋ฒ์งธ ํ๋ก์ ํธ : ๋ ์จ ์ ๋ณด ๋ฐ์์ค๊ธฐ

## ํ๋ก์ ํธ ๊ฐ๋จ ์ค๋ช

- API๋ฅผ ์ฌ์ฉํ์ฌ ๋ ์จ ์ ๋ณด๋ฅผ ์ถ๋ ฅํ๋ ํ๋ก๊ทธ๋จ

<br>

## ํ๋ก์ ํธ ์ฝ๋ฉํ๊ธฐ

### 1. (์ฌ์  ์ค๋น) API key ํ์ฑํ ํ๊ธฐ

- https://home.openweathermap.org/users/sign_up ์ ์ํ ํ ํ์๊ฐ์
- ๋ก๊ทธ์ธ ํ๊ธฐ
- API key ๋ฐ๊ธ๋ ๊ฒ ํ์ธํ๊ธฐ

<br>

### 2. API๋?

- API (Application Programmin Interface) : ํ๋ก๊ทธ๋จ๊ณผ ํ๋ก๊ทธ๋จ์ ์ฐ๊ฒฐํด์ฃผ๋ ๊ฒ
- ์ฌ์ฉํ  API : OpenWeatherMap (์ธ๊ณ์ ๋ ์จ๋ฅผ ๋ชจ๋ ๋ณผ ์ ์๋ API)
- Open API : ๋๊ตฌ๋ ์ฌ์ฉํ  ์ ์๋๋ก ๊ณต๊ฐํ API
- API key : API๋ฅผ ์ฌ์ฉํ ์ฌ๋๋ค์ ๊ธฐ๋ก

<br>

### 3. API ๋งํฌ ๋ง๋ค๊ธฐ

```python
city = "Seoul"
apikey = "################################"
api = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={apikey}"
```

<br>

### 4. ๋ ์จ ๋ฐ์์ค๊ธฐ

- requests๋ก ์์ฒญํ๊ธฐ

```python
import requests

...

result = requests.get(api)
```

- python json ๋ชจ๋ ์ฌ์ฉํ๊ธฐ
  - json (JavaScript Object Notation) : ๋ฐ์ดํฐ๋ฅผ ์ฃผ๊ณ  ๋ฐ์ ๋ ์ฌ์ฉํ๋ ํฌ๋งท
  - ๋์๋๋ฆฌ ํํ

```python
import json

data = json.loads(result.text)  # ๋ฐ์์จ ์๋ต๊ฐ์ json ํํ๋ก ๋ณํ
```

<br>

### 5. ์์๊ฒ ์ ๋ฆฌํ๊ธฐ

```python
# ๋ ์จ
print(data["name"], "์ ๋ ์จ์๋๋ค.")  # Seoul์ ๋ ์จ์๋๋ค.
print("๋ ์จ๋ ", data["weather"][0]["main"], "์๋๋ค.")  # ๋ ์จ๋ Clouds ์๋๋ค.

# ์จ๋
print("ํ์ฌ ์จ๋๋ ",data["main"]["temp"],"์๋๋ค.")  # ํ์ฌ ์จ๋๋ 302.29 ์๋๋ค.
print("ํ์ง๋ง ์ฒด๊ฐ ์จ๋๋ ",data["main"]["feels_like"],"์๋๋ค.")  # ํ์ง๋ง ์ฒด๊ฐ ์จ๋๋ 306.81 ์๋๋ค.
```

- language ํ๋ผ๋ฏธํฐ ์ถ๊ฐํด์ ์ธ์ด ๋ฐ๊พธ๊ธฐ

```python
lang = "kr"

api = f"""http://api.openweathermap.org/data/2.5/\
weather?q={city}&appid={apikey}&lang={lang}"""
```

- units ํ๋ผ๋ฏธํฐ ์ถ๊ฐํด์ ์จ๋ ๋จ์ ๋ฐ๊พธ๊ธฐ (ํ์จ -> ์ญ์จ)

```python
api = f"""http://api.openweathermap.org/data/2.5/\
weather?q={city}&appid={apikey}&lang={lang}&units=metric"""
```

<br>

## ์ ์ฒด ์ฝ๋

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

# ์ง์ญ : name
print(data["name"],"์ ๋ ์จ์๋๋ค.")
# ์์ธํ ๋ ์จ : weather - description
print("๋ ์จ๋ ",data["weather"][0]["description"],"์๋๋ค.")
# ํ์ฌ ์จ๋ : main - temp
print("ํ์ฌ ์จ๋๋ ",data["main"]["temp"],"์๋๋ค.")
# ์ฒด๊ฐ ์จ๋ : main - feels_like
print("ํ์ง๋ง ์ฒด๊ฐ ์จ๋๋ ",data["main"]["feels_like"],"์๋๋ค.")
# ์ต์  ๊ธฐ์จ : main - temp_min
print("์ต์  ๊ธฐ์จ์ ",data["main"]["temp_min"],"์๋๋ค.")
# ์ต๊ณ  ๊ธฐ์จ : main - temp_max
print("์ต๊ณ  ๊ธฐ์จ์ ",data["main"]["temp_max"],"์๋๋ค.")
# ์ต๋ : main - humidity
print("์ต๋๋ ",data["main"]["humidity"],"์๋๋ค.")
# ๊ธฐ์ : main - pressure
print("๊ธฐ์์ ",data["main"]["pressure"],"์๋๋ค.")
# ํํฅ : wind - deg
print("ํํฅ์ ",data["wind"]["deg"],"์๋๋ค.")
# ํ์ : wind - speed
print("ํ์์ ",data["wind"]["speed"],"์๋๋ค.")
```

<br>
<br>
<br>

# ๐ ์ธ ๋ฒ์งธ ํ๋ก์ ํธ : ๋ฒ์ญ๊ธฐ ํ๋ก๊ทธ๋จ

## ํ๋ก๊ทธ๋จ ๊ฐ๋จ ์ค๋ช

- ํ๊ธ -> ์์ด๋ก ๋ฒ์ญํด์ฃผ๋ ํ๋ก๊ทธ๋จ

<br>

## ํ๋ก๊ทธ๋จ ์ฝ๋ฉํ๊ธฐ

### 1. Googletrans๋?

- ์ธ์ด ๊ฐ์ง ๋ฐ ๋ฒ์ญ ๊ธฐ๋ฅ์ ๊ฐ์ง ๋ผ์ด๋ธ๋ฌ๋ฆฌ

```python
from googletrans import Translator
```

<br>

### 2. ์ธ์ด ๊ฐ์งํ๊ธฐ

- ๋ฒ์ญ๊ธฐ๋ฅผ ๋ง๋ ๋ค.

```python
translator = Translator()
```

- ์ธ์ด ๊ฐ์ง๋ฅผ ์ํ๋ ๋ฌธ์ฅ์ ์ค์ ํ๋ค.

```python
sentence = "์๋ํ์ธ์. ์ฝ๋๋ผ์ด์ธ์๋๋ค."
```

- ์ธ์ด๋ฅผ ๊ฐ์งํ๋ค.

```python
detected = translator.detect(sentence)
print(detected)  # Detected(lang=ko, confidence=1.0) -> confidence : ์ ๋ขฐ์ฑ

# ์ธ์ด๋ง
print(detected.lang)  # ko
```

- ์ฌ์ฉ์์๊ฒ ์ง์  ์๋ ฅ๋ฐ์ ๋ฌธ์ฅ์ ์ธ์ด ๊ฐ์ง

```python
sentence = input("์ธ์ด๋ฅผ ๊ฐ์งํ  ๋ฌธ์ฅ์ ์๋ ฅํด์ฃผ์ธ์ : ")
detected = translator.detect(sentence)

print(detected.lang)
```

<br>

### 3. ๋ฌธ์ฅ ๋ฒ์ญํ๊ธฐ

- ๋ฒ์ญ๊ธฐ๋ฅผ ๋ง๋ ๋ค.
- ๋ฒ์ญ์ ์ํ๋ ๋ฌธ์ฅ์ ์ค์ ํ๋ค.
- ๋ฒ์ญ์ ์ํ๋ ์ธ์ด๋ฅผ ์ค์ ํ๋ค.
- ๋ฒ์ญํ๋ค.
- translate(๋ฒ์ญํ  ๋ฌธ์ฅ, ๋ฒ์ญํ  ์ธ์ด, ํ์คํธ์ ์ธ์ด(์๋ต๊ฐ๋ฅ))

```python
result = translator.translate(sentence, 'en')
print(result)  # Translated(src=ko, dest=en, text=hello, this is codelion., pronunciation=None, extra_data="{'transla...}")
```

```python
print(detected.lang, ":", sentence)  # ko: ์๋ํ์ธ์, ์ฝ๋๋ผ์ด์ธ์๋๋ค.
print(result.dest, ":", result.text)  # en: Hello, this is codelion.
```

<br>

## ์ ์ฒด ์ฝ๋

```python
from googletrans import Translator

translator = Translator()

# sentence = "์๋ํ์ธ์ ์ฝ๋๋ผ์ด์ธ์๋๋ค."
sentence = input("๋ฒ์ญ์ ์ํ๋ ๋ฌธ์ฅ์ ์๋ ฅํด์ฃผ์ธ์ : ")
dest = input("์ด๋ค ์ธ์ด๋ก ๋ฒ์ญ์ ์ํ์๋์?")

result = translator.translate(sentence,dest)
detected = translator.detect(sentence)

print("===========์ถ ๋ ฅ ๊ฒฐ ๊ณผ===========")
print(detected.lang,":",sentence)
print(result.dest,":",result.text)
print("=================================")
```

<br>
<br>
<br>

# 4. โ ๋ค ๋ฒ์งธ ํ๋ก์ ํธ : ๋ฉ์ผ ๋ณด๋ด๊ธฐ

## ํ๋ก์ ํธ ๊ฐ๋จ ์ค๋ช

- ๋ฉ์ผ์ด ์๋์ผ๋ก ์ ์ก๋๋ ํ๋ก๊ทธ๋จ

<br>

## ํ๋ก์ ํธ ์ฝ๋ฉํ๊ธฐ

### 1. ์ฌ์  ์ค๋น

- Gmail IMAP ์ฌ์ฉ ์ค์ ํ๊ธฐ : IMPA ์ฌ์ฉ ํ๊ฐ๋ก ๋ฐ๊พธ๊ธฐ
- ๋ฉ์ผ ๊ณ์ ์ ์ธ๋ถ ์ ์์ ๋ํ ๋ณด์ ์ค์  : ๊ณ์  ๊ด๋ฆฌ > ๋ณด์ > ๋ณด์ ์์ค์ด ๋ฎ์ ์ฑ์ ์์ธ์ค ํ์ฉ

<br>

### 2. SMTP (Simple Mail Transfer Protocol)

- ํด๋ผ์ด์ธํธ(๋ค๋ฅธ ์๋ฒ)์์ ์ด๋ฉ์ผ ์๋ฒ๋ก ๋ฉ์ผ์ ๋ณด๋ผ ๋ ์ฌ์ฉ
- IMAP : ์ด๋ฉ์ผ ์๋ฒ์์ ํด๋ผ์ด์ธํธ๋ก ์ด๋ฉ์ผ ๋ณด๋ผ ๋ ์ฌ์ฉ
- SMTP ์๋ฒ(์ด๋ฉ์ผ ์๋ฒ)๋ฅผ ์ด์ฉํด์ ์ฐ๋ฆฌ๊ฐ ์ํ๋ ๊ณณ์ผ๋ก ๋ฉ์ผ์ ๋ณด๋ผ ์ ์๋ค.
- ์์

  - SMTP ๋ฉ์ผ ์๋ฒ๋ฅผ ์ฐ๊ฒฐํ๋ค.

  ```python
  import smtplib

  SMTP_SERVER = "smtp.gmail.com"
  SMTP_PORT = 465

  # ์๋ฒ์ ์ฐ๊ฒฐ
  smtp = smtplib.SMTP_SSL(SMTP_SERVER, SMTP_PORT)
  ```

  - SMTP ๋ฉ์ผ ์๋ฒ์ ๋ก๊ทธ์ธํ๋ค.

  ```python
  smtp.login("###@gmail.com", "#######")  # ์ด๋ฉ์ผ, ๊ตฌ๊ธ ๋น๋ฐ๋ฒํธ
  ```

  - SMTP ๋ฉ์ผ ์๋ฒ๋ก ๋ฉ์ผ์ ๋ณด๋ธ๋ค.

  ```python
  smtp.send_message()  # ๋ฉ์ผ ๋ด์ฉ
  ```

<br>

### 3. MIME

- SMTP์ ๋ฉ์ผ์ ๋ณด๋ด๊ธฐ ์  ๋ฉ์ผ ๋ด์ฉ์ MIME ํํ๋ก ๋ฐ๊ฟ์ผ ํจ
- email.message ๋ชจ๋ : .EmailMessage ๊ธฐ๋ฅ ์ฌ์ฉํด์ MIME ํํ๋ก ๋ฐ๊พผ๋ค.
- ์์

  - ์ด๋ฉ์ผ์ ๋ง๋ ๋ค.

  ```python
  from email.message import EmailMessage

  message = EmailMessage()
  ```

  - ์ด๋ฉ์ผ์ ๋ด์ฉ์ ๋ด๋๋ค.

  ```python
  # CONTENT
  message.set_content("์ฝ๋๋ผ์ด์ธ")  # ๋ฉ์์ง ๋ด์ฉ
  ```

  - ๋ฐ์ ์, ์์ ์๋ฅผ ์ค์ ํ๋ค.

  ```python
  # HEADER
  message["Subject"] = "์ ๋ชฉ"
  message["From"] = "###@gmail.com"  # ๋ฐ์ ์
  message["To"] = "***@gmail.com"  # ์์ ์
  ```

<br>

### 4. ๋ฉ์ผ ์ ์กํ๊ธฐ

```python
smtp.send_message(message)
```

<br>

### 5. ๋ฉ์ผ์ ์ฌ์ง ์ฒจ๋ถํ๊ธฐ

- ์ด๋ฏธ์ง ํ์ผ ์ฝ์ด์ค๊ธฐ
  - rb : read binary
  - wb : write binary
  - ab : append binary

```python
# close๋ฌธ ์์ด ์ฝ๊ณ  ์ธ ์ ์์
with open("codelion.png", "rb") as image:
    image_file = image.read()
```

- add_attachment() : text๊ฐ ์๋ ๋ค๋ฅธ ํ์ผ๋ค์ ์ฒจ๋ถํ  ๋ ์ฌ์ฉ (MIME MIXED ํ์)
  - image : ์ฒจ๋ถํ  ๋ด์ฉ
  - maintype : ์ฒจ๋ถํ  ๋ด์ฉ์ ์ ํ (img, vid , ...)
  - subtype : ํ์ฅ์ (png, mp4, ...)

```python
message.add_attachment(image_file, maintype='image', subtype=image_type)  # subtype์ ๋ฐ์ ์ฐธ๊ณ 
```

- image์ ํ์ฅ์๊ฐ ๊ณ์ ๋ณํ  ๋ ์ฌ์ฉํ  ์ ์๋ ๋ชจ๋

```python
import imghdr

image_type = imgher.what('codelion', image_file)  # ์ด๋ค ํ์ฅ์์ธ์ง ํ์
```

<br>

### 6. ์ ํจ์ฑ ๊ฒ์ฌํ๊ธฐ

- ๋ณด๋ด๊ณ ์ ํ๋ ์ด๋ฉ์ผ ์ฃผ์๊ฐ ์ ํจํ์ง ๊ฒ์ฌ / ํ๋จ
- ์ ๊ทํํ์ : ๋ฌธ์์ด์์ ๋ํ๋๋ ์ผ์ ํ ํจํด ํ์ ํ ๋์
  - ์ด๋ฉ์ผ์์๋ง ๋ํ๋๋ ์ผ์ ํ ํจํด์ ์กฐ๊ฑด์ผ๋ก ์ฃผ๊ณ  ์ด ์กฐ๊ฑด์ ๋ฌธ์์ด์ด ์ ํฉํ์ง ํ๋จ

<br>

๐ง ์ด๋ฉ์ผ์ ์ ๊ท ํํ์

```
^[a-zA-Z0-9.+_-]+@[a-zA-Z0-9]+\.[a-zA-Z]{2,3}$
```

- ^ : ์์, $ : ๋
- ์ฒซ ๋ฒ์งธ [ ] : a๋ถํฐ z๊น์ง, A๋ถํฐ Z๊น์ง, 0๋ถํฐ 9๊น์ง, ., +, \_, - ๊ฐ 1ํ ์ด์ ๋ฐ๋ณต๋๋ค.
- @ : ๊ทธ ๋ค์ @๊ฐ ๋ถ๋๋ค.
- a๋ถํฐ z๊น์ง, A๋ถํฐ Z๊น์ง, 0๋ถํฐ 9๊น์ง๊ฐ 1ํ ์ด์ ๋ฐ๋ณต๋๋ค.
- \. : ๊ทธ ๋ค์ .์ด ๋ถ๋๋ค.
- a๋ถํฐ z๊น์ง, A๋ถํฐ Z๊น์ง๊ฐ ์ต์ 2ํ, ์ต๋ 3๋ฒ ๋ฐ๋ณต๋๋ค.

<br>

- ์ ๊ทํํ์ ์ฌ์ฉํ๊ธฐ ์ํด์๋ re ๋ชจ๋ import

```python
import re

reg = "^[a-zA-Z0-9.+_-]+@[a-zA-Z0-9]+\.[a-zA-Z]{2,3}$"
print(re.match(reg, "codelion.examplegmailcom"))  # None
print(re.match(reg, "codelion.example@gmail.com"))
```

- ์ ํจ์ฑ ๊ฒ์ฌ ํ ๋ฉ์ผ ๋ณด๋ด๊ธฐ
  - ์ ํจํ๋ค๋ฉด ๋ฉ์ผ ๋ณด๋ด๊ธฐ
  - ์ ํจํ์ง ์๋ค๋ฉด ๋ฉ์ผ ๋ณด๋ด์ง ์๊ธฐ

```python
def sendEmail(addr):
    reg = "^[a-zA-Z0-9.+_-]+@[a-zA-Z0-9]+\.[a-zA-Z]{2,3}$"
    if bool(re.match(reg, addr)):
        smtp.send_message(message)
        print("์ ์์ ์ผ๋ก ๋ฉ์ผ์ด ๋ฐ์ก๋์์ต๋๋ค.")
    else:
        print("์ ํจํ ์ด๋ฉ์ผ ์ฃผ์๊ฐ ์๋๋๋ค.")

sendEmail("###@gmail.com")
```

<br>

## ์ ์ฒด ์ฝ๋

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
        print("์ ์์ ์ผ๋ก ๋ฉ์ผ์ด ๋ฐ์ก๋์์ต๋๋ค.")
    else:
        print("์ ํจํ ์ด๋ฉ์ผ ์ฃผ์๊ฐ ์๋๋๋ค.")

message = EmailMessage()
message.set_content("์ฝ๋๋ผ์ด์ธ ์์์ค์๋๋ค.")

message["Subject"] = "์ด๊ฒ์ ์ ๋ชฉ์๋๋ค."
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
