<img width="942" alt="KakaoTalk_20220522_202040221 복사" src="https://user-images.githubusercontent.com/83055813/169692734-c7641655-5757-4c80-ad5d-279adb511afc.png">

<br>

# 자바스크립트 기초

## 자바스크립트란?
- 웹브라우저에서 사용하기 위해 만들어진 프로그래밍 언어
- 지금은 웹에만 국한되지 않고 서버에서도 사용

<br>
<br>
<br>

## 변수와 상수
- let, const

### 1. 변수

- 값을 저장할 수 있는 메모리 공간
- 변수의 쓰임에 맞게 변수명 지정 
- 변수명이 2단어 이상이면 2번째 단어는 대문자로 시작 (Camel case)
- 변수의 재할당 : 변수의 값을 선언 후 다른 값으로 재선언

<br>

## 자료형과 연산자

### 1. 자료형 (Data type)

- 숫자 (Number) 
- 문자열 (String) : 작은따옴표나 큰따옴표로 감싸서 사용
- 참/거짓 (Boolean) : True(참) / False(거짓)
- Null / undefined
    - undefined : 변수를 선언 후 값을 아직 할당하지 않은 상태
    - Null : 변수를 선언 후 빈 값을 할당한 상태

<br>

### 2. 연산자 (Operators)

- 산술 연산자 
    - +(더하기), -(빼기), *(곱하기), /(나누기, 몫), %(나머지)
- 문자결합 연산자
    - 피연산자가 하나라도 문자라면 문자로 결합
    - +연산자 사용
- 대입 연산자
    - =, +=, -=, *=, /=, %=
- 증감 연산자
    - 숫자형 데이터를 1씩 증가하거나 감소
    - 피연산자가 하나만 필요
    - 증감 연산자가 뒤에 올 때 : 해당 줄이 끝나고 난 후에 1을 더하거나 빼기
    - 증감 연산자가 앞에 올 때 : 바로 1을 더하거나 빼서 해당 변수에 할당
- 비교 연산자
    - <, >, <=, =>, ==, !=, === (자료형까지 같은지 확인), !== (자료형까지 같은지 확인)
- 논리 연산자
    - ||(or), &&(and), !(not)

<br>

### 3. 연산자 우선순위
1. ()
2. 단항 연산자 (--, ++, !)
3. 산술 연산자
4. 비교 연산자
5. 논리 연산자
6. 대입 연산자

<br>
<br>
<br>

## 제어문

### 1. 조건문
- if문 : 조건식이 참일 때만 실행
    - if (조건식) { 실행문 }
- else문 : if문의 조건식이 참일때는 if문 실행, 거짓일 때 else문 실행
- else if문 : 조건이 여러개일때 사용

<br>

### 2. 반복문
- while문
    - 조건식을 만족하면 중괄호 안 코드와 증감식 실행
    - 그리고 다시 조건식 검사
    - 조건식이 false가 되면 반복문을 빠져나감
    - 주의사항 : 무한 루프에 빠지지 않게끔 조건문이 언젠가는 false가 되어야 함
```javascript
let 변수 = 초기값;
while (조건식) {
    코드;
    증감식;
}
```
- for문
    - 초기값 → 조건식 → 자바스크립트 코드 → 증감식 → 조건식 → true이면 실행, false이면 끝
```javascript
for (let i = 0; i < 10; i++){
    console.log(i);
}
```

<br>

### 3. break와 continue
- break : 반복문 안에서 사용하면 조건식과 상관없이 강제 종료
- continue : continue 그 다음 코드 무시하고 바로 조건식으로 이동

<br>
<br>
<br>

## 함수와 객체

### 1. 함수 (Function)
- 필요한 기능, 자주 사용할 것 같은 기능들을 하나의 명령어로 실행할 수 있도록 해줌
- 함수 선언 : 함수가 어떤 명령어를 처리해야할 지 미리 알려줌
- 함수 실행 : 선언한 함수를 가져와 사용
```javascript
function add(num1, num2) {
    return num1 + num2;
}
const sum1 = add(100, 200);  // 300

function hellp(name) {
    console.log(`Hello, +${name}`);
}
hello('lion');  // Hello, lion
```

<br>

### 2. 객체 (Object)
- 하나의 변수에 여러 정보를 담을 수 있음
- 키와 값으로 구성
```javascript
const sample = {
    'key with space': true,
    name: 'likelion',
    age: 20
};

console.log(sample.name);  // likelion
```

<br>
<br>
<br>

## 배열

### 1. 배열
- 여러 개의 데이터를 한 곳에 저장
- 배열 안의 데이터를 인덱스로 접근
```javascript
const numArray = [1, 2, 3, 4, 5];

console.log(numArray[2]);  // 3
```

<br>
<br>
<br>

# HTML + JS

## DOM (Document Object Model)

### 1. DOM이란?
- DOM은 HTML을 파싱한 결과물
    - 브라우저에 리퀘스트를 보내서 서버에서 응답한 HTML 문서는 문자열로 이루어진 순수한 텍스트 형태 -> 브라우저가 이해하지 못함
    - 서버는 HTML 파일을 메모리에 저장한 다음 메모리에 저장된 바이트를 리스폰스함
    - HTML 내에 선언된 인코딩 방식에 따라 문자열로 변환
    - 이를 문법적 의미를 갖는 코드의 최소 단위인 토큰들로 분해
    - 각 토큰들을 객체로 변환하여 노드 생성 -> 이 노드가 DOM을 구성하는 가장 기본 요소
    - HTML 요소는 중첩 관계를 가지기도 하는데 이때 부모와 자식 관계 형성 -> 이러한 관계를 포함하여 모든 노드의 관계들을 tree 자료구조로 구성 이때 이 tree를 DOM이라고 부른다.
- 이 DOM api를 통해서 HTML의 구조, 내용, 스타일등을 동적으로 조작 가능

<br>

### 2. DOM 요소 노드 취득
- document.getElementById('id값'); 
    - id를 이용한 요소 노드 취득
- document.getElementByTagName('태그 이름');
    - 인수에 들어있는 태그 이름을 갖는 모든 요소 노드들을 탐색하여 반환 (HTMLCollection 객체 반환)
- document.getElementsByClassName('class 값');
    - 인수로 전달한 클래스 값을 갖는 모든 요소 노드들을 탐색하여 반환 (HTMLCollection 객체 반환)
- document.querySelector('css 선택자');
- document.querySelectorAll('css 선택자');
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <ul>
        <li id="lion">lion</li>
        <li id="tiger">tiger</li>
        <li id="bear">bear</li>
    </ul>
    
    <script src="practice.js"></script>
</body>
</html>
```
```javascript
// lion -> red
document.getElementById('lion').style.color = "red";
// tiger -> blue
document.getElementById('tiger').style.color = "blue";
// bear -> green
document.getElementById('bear').style.color = "bear";
```

<br>

### 3. DOM 조작
- DOM에 새로운 노드를 추가하거나 기존 노드의 삭제나 교체를 의미
- innerHTML : 요소 노드의 HTML 마크업을 취득하거나 변경 
- classList : 특정 요소에 클래스 추가
```html
<ul>
    <li id="lion">lion</li>
    <li id="tiger">tiger</li>
    <li id="bear">bear</li>
</ul>
<div class="box"></div>
```
```css
.purple {
    background-color: purple;
}
.yellow {
    background-color: yellow;
}
```
```javascript
// bear -> dog
document.querySelectorAll("animal")[2].innerHTML = "dog";
// background-color -> purple
docment.querySelectorAll(".box")[0].classList.add("purple");
// purple 삭제
docment.querySelectorAll(".box")[0].classList.remove("purple");

// toggle 
docment.querySelectorAll(".box")[0].classList.toggle("yellow");
```

<br>
<br>
<br>

## Event
- 어떤 사건을 발생 시키는 것  

<br>

### 1. 이벤트 타입
- 이벤트 종류를 나타내는 문자열

<br>

### 2. 이벤트 핸들러
- 이벤트가 발생했을 때 실행되는 함수

<br>

### 3. addEventListener
- EventTarget.addEventListener('eventType', function, useCapture);
    - EventTarget : 이벤트 타깃
    - eventType : 이벤트 타입
    - function : 이벤트 핸들러
    - useCapture : 캡쳐 사용 여부
```html
<button id="plus">+</button>
<span id="num">0</span>
<button id="minus">-</button>
```
```js
var num = 0;

document.getElementById("plus").addEventListener("click", 
    num++;
    document.getElementById("num").innerHTML = num;
);

document.getElementById("minus").addEventListener("click", 
    num--;
    document.getElementById("num").innerHTML = num;
);
```

<br>

### 4. data 어트리뷰트와 dataset 프로퍼티
- data 어트리뷰트와 dataset 프로퍼티를 활용하면 HTML에서 정의한 사용자 어트리뷰트와 자바스크립트 간의 데이터를 교환할 수 있음
- data-속성명 = "속성값"
```html
<body>
    <ul id="users">
        <li data-user-id="hello1" data-role="subscriber">chaebin</li>
    </ul>
</body>
```

<br>

### 5. 이벤트 객체
- 이벤트가 발생하면 이벤트의 정보를 담고 있는 이벤트 객체가 동적으로 생성
- 이때 생성된 이벤트 객체는 이벤트 핸들러의 첫 번째 인수로 전달됨
```html
<p class = "msg">where?</p>
<script>
    const msg = document.querySelector('.msg');
    function showWhere(e) {
        msg.innerHTML = `my location is ${e.clientX}, ${e.clientY}`;
    }
    document.onClick = showWhere;
```

<br>

### 6. scroll 이벤트
- 스크롤바를 조작할 때 발생하는 이벤트
- window.addEventListener('scroll', function() {});
- scrollHeight : 전체부분
- clientHeight : 스크롤을 통해 보여지는 부분
- scrollTop : 박스가 보이는 높이를 포함하지 않은 채 스크롤 바를 내린 양

<br>
<br>
<br>

## 타이머

### 1. 타이머 함수
- 호출 스케줄링 : 일정 시간 후에 함수가 호출되도록 하는 함수
- setTimeout (타이머가 만료된 후에 호출될 콜백함수 or 문자열, 시간)
    - 한번만 호출
- setInterval (타이머가 만료된 후에 호룿로딜 콜백함수 or 문자열, 시간)
    - 일정한 시간을 두고 반복하면서 호출
```html
<div class="timeout">7초 후에 내가 사라져볼게 얍</div>
<script>
    let timecnt = 7;
    setInterval(function() {
        timecnt--;
        document.querySelector('.timeout').innerHTML = `${timecnt}초 후에 내가 사라져볼게 얍`;
    }, 1000);
    setTimeout(function() {
        document.querySelector('.timeout').style.display = "none";
    }, 7000);
```
