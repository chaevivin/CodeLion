### 파이썬의 장점

- 파이썬은 가장 대중화된 언어이자 가장 좋은 평가를 받고 있는 언어
- 파이썬 생태계가 크기 때문에 선택의 폭이 넓다.

<br>

# 🥗 첫번째 프로젝트 : 오늘은 뭐 드실?

## 프로젝트 간단 설명

- 점심 / 저녁을 골라주는 프로그램
- 프로그램을 실행하면 기본 메뉴가 나옴
- 첫번째 단계 : 메뉴 추가
- q를 누르면 메뉴 추가가 끝나고 최종 메뉴 후보 나옴
- 두번째 단계 : 메뉴 삭제
- q를 누르면 메뉴 삭제가 끝나고 최종 메뉴 후보 나옴
- 엔터를 누르면 5초 후 랜덤으로 메뉴 자동 선택

<br>

## 프로젝트 코딩하기

### 1. 랜덤으로 뽑기

- import random : random 함수를 사용
- random.choice : 리스트에서 랜덤으로 하나 선택

```python
import random

print(random.choice(["피자", "치킨", "햄버거"]))
```

<br>

### 2. 반복하기

- 음식 30번 뽑기

```python
import random

for i in range(30):
  print(random.choice(["피자", "치킨", "햄버거"]))
```

<br>

### 3. 데이터 상자 만들기 (변수)

- 점심과 저녁 구분하여 데이터에 이름 붙이기
- 데이터 이름으로 데이터 불러오기
- 변수를 바꾸기 위해서는 데이터 삭제 안해도 됨

```python
lunch = random.choice(["된장찌개", "피자", "제육볶음"])
dinner = random.choice(["김밥", "쫄면", "돈까스"])

print(lunch)
```

<br>

### 4. 사용자에게 입력받은 데이터 추가

- input() 사용
- 사용자에게 입력 받은 값을 item 변수에 저장
- lunch 리스트에 item 추가
- 여러번 반복
- 'q'가 입력되면 while문 멈춤

```python
lunch = ["된장찌개", "피자", "제육볶음", "짜장면"]

while True:
  print(lunch)
  item = input("음식을 추가해주세요 : ")
  if(item == 'q'):
  break
  else:
  lunch.append(item)

print(lunch)
```

<br>

### 5. 사용자에게 입력받은 데이터 삭제

- 집합 사용
- 차집합으로 데이터 삭제

```python
#이어서

set_lunch = set(lunch)
while True:
  print(set_lunch)
  itme = input("음식을 삭제해주세요. : ")
  if(item == 'q'):
  break
else:
  set_lunch = set_lunch - set([item])
```

<br>

### 6. 랜덤으로 선택

- 5초 세기
- 집합을 리스트로 변경 (set_lunch)
- random.choice()로 랜덤으로 뽑기
- time과 random을 사용하기 위해서 import time, random

```python
#이어서

print(set_lunch, "중에서 선택합니다.")

for i in range(5, 0, -1):
  print(i)
  time.sleep(1)

print(random.choice(list(set_lunch)))
```

<br>

## 전체 코드

```python
import time
import random

lunch = ["된장찌개", "피자", "제육볶음", "짜장면"]

while True:
  print(lunch)
  item = input("음식을 추가해주세요 : ")
  if(item == 'q'):
  break
else:
  lunch.append(item)

print(lunch)

set_lunch = set(lunch)
while True:
  print(set_lunch)
  itme = input("음식을 삭제해주세요. : ")
  if(item == 'q'):
  break
else:
  set_lunch = set_lunch - set([item])

print(set_lunch, "중에서 선택합니다.")

for i in range(5, 0, -1):
  print(i)
  time.sleep(1)

print(random.choice(list(set_lunch)))
```

<br>
<br>
<br>

# 📝 두번째 프로젝트 : 익명 질문 게시판

## 프로젝트 간단 설명

- 질문하고 답변하는 프로그램
- 질문 입력받기
- 'q'를 입력하면 질문을 그만 받고 대답으로 넘어감
- 대답으로 넘어가면 앞의 질문들이 나옴
- 모든 질문에 대답을 하면 질문과 대답을 정리해서 출력

<br>

## 프로젝트 코딩하기

### 1. 함수

- 형태
  ```python
  def 함수이름():
    함수가 해야할 내용 1
    함수가 해야할 내용 2
  ...
  ```

<br>

### 2. 데이터 저장

- 질문과 대답 2가지 데이터 저장하기
- 딕셔너리 형태
- key로 question

```python
total_dictionary = {}

while True:
  question = input("질문을 입력해주세요 : ")
  if(question == 'q'):
  break
else:
  total_dictionary[question] = ""

print(total_dictionary)
```

<br>

### 3. 답변 받기

- 질문을 돌면서 답변 받기
- for문 사용

```python
#이어서

for i in total_dictionary:
  print(i)
  answer = input("답변을 입력해주세요 : ")
  total_dictionary[i] = answer
```

<br>

### 4. 데이터 다른 방식으로 저장하기

- 전체 데이터 리스트로 관리 -> 안의 데이터는 딕셔너리로 관리
- key : 질문, 답변 | value : 입력받은 질문, 답변
- total_list를 접근할 때 i의 key값으로 value 접근

```python
total_list = []

while True:
  question = input("질문을 입력해주세요 : ")
  if(question == 'q'):
  break
else:
  total_list.append({"질문" : question, "답변" : ""})

for i in total_list:
  print(i["질문"])
  answer = input("답변을 입력해주세요 : ")
  i["답변"] = answer

print(total_list)
```

<br>

## 전체 코드

```python
total_list = []

while True:
  question = input("질문을 입력해주세요 : ")
  if(question == 'q'):
  break
else:
  total_list.append({"질문" : question, "답변" : ""})

for i in total_list:
  print(i["질문"])
  answer = input("답변을 입력해주세요 : ")
  i["답변"] = answer

print(total_list)
```
