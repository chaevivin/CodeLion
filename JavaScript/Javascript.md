<img width="888" alt="KakaoTalk_20220528_020737224 복사" src="https://user-images.githubusercontent.com/83055813/170751948-9d1f3857-4db1-4fbb-9e5e-2c194a5616d1.png">

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

<br>
<br>
<br>

# 자바스크립트 심화

## 타입 변환
- 자바스크립트는 상황에 따라 자동으로 타입 변환이 됨 
- 자바스크립트는 데이터 타입을 자기가 맞다고 생각하는대로 변환
- 그래서 우리는 보다 정확하게 데이터 타입을 넘겨줘야 함
```js
console.log("7" * "4");  // 28
console.log("7" + "4");  // "74"
console.log("Hello" * "World");  // NaN (Not a Number)
```

<br>
<br>
<br>

## Truthy and Falsy
- Truthy : True 같은 것
- Falsy : False 같은 것

### 1. not 연산자
```js
!""  // true
!"hello"  // false
!undefined  // true
!null  // true
!0  // true
!NaN  // true
```
- 빈문자열 = false, 문자열 = true

<br>
<br>
<br>

## 함수
- 수학의 함수와 자바스크립트 함수의 차이점
    - 입력과 출력이 선택적 (입력만, 출력만, 둘다, 둘다x 가능)
    - side-effect (부가 기능)이 있어도 된다 

### 1. 화살표 함수 (Arrow-function)
```javascript
function add(a, b) {
    return a + b;
}
```
```js
const add = (a, b) => {
    return a + b;
}
```
```js
const add = (a, b) => a + b;
```

<br>

### 2. 일급 객체 (First-class citizen)
- 해당 타입이 변수에 할당될 수 있어야 한다.
- 해당 타입이 함수의 인자로 넘어갈 수 있어야 한다.
- 해당 타입이 함수의 반환값으로 반환될 수 있어야 한다.
- JS의 데이터타입(숫자, 문자열, 불리언, null, undefined) 전부 일급객체
- 함수 또한 일급객체 ex) addEventListener

<br>
<br>
<br>

## 비동기 promise

### 1. 비동기
- 동기 : 동시에 일어남 -> 요청한 그 자리에서 결과값 반환
- 비동기 : 동시에 일어나지 않음 -> 요청한 그 자리에서 결과값 반환하지 않아도 됨
```js
// 비동기
fetch("https://jsonplaceholder.typicode.com/posts/1")  // 데이터를 다 받아온 후
    .then(res => res.json())  // json 형태로 변환 후
    .then(console.log);  // console에 출력
```

<br>

### 2. 프로미스 (promise)
- 비동기 처리 방식
- 프로미스의 상태
    - Pending : 프로미스 처리 중
    - Fulfilled : 프로미스 이행 (정상처리완료)
    - Rejected : 프로미스 실패 (처리완료, 하지만 비정상적으로)
- .then(함수)

<br>
<br>
<br>

## 논리 연산자 심화

### 1. &&
- 처음 나오는 falsy 값을 반환한다. 만약 둘 다 truthy라면, 마지막 값을 반환한다.
```js
me.militaryState !== undefined && console.log("거짓");  
// &&를 기준으로 앞이 true이면 console.log 실행
```

<br>

### 2. ||
- 처음 나오는 truthy 값을 반환한다. 만약 둘 다 falsy라면, 마지막 값을 반환한다.
- ||를 기준으로 앞이 true이면 뒤 실행 x
- ||를 기준으로 앞이 false이면 뒤 실행

<br>
<br>
<br>

## 비구조화 할당 (destructuring)
- 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식
- 어떤 객체의 키 값을 새로운 변수로 선언하고 싶을 때 사용
```js
const me {
    name: "정채빈",
    age: 25,
};

const name = me.name;
const age = me.age;

const { name, age } = me;  // 비구조화 할당
```
- 배열에서도 사용 가능
```js
const a = arr[0];
const b = arr[1];

const [a, b] = arr;  // 비구조화 할당
```

<br>
<br>
<br>

## 스프레드 (spread)
- 배열, 문자열, 객체 등 반복 가능한 객체 (Iterable Object)를 개별 요소로 분리할 수 있다.
- 객체는 객체에서만, 배열은 배열에서만 사용 가능
```js
const me = {
    name: "정채빈",
    age: 25,
};

const newMe = {
    ...me,  // me 객체의 키와 값들을 모두 가지고 옴
    gender: "female",  
};
```
```js
const animals = ["강아지", "고양이"];
const anotherAnimals = [...animals, "햄스터"];  // 강아지, 고양이, 햄스터
```

<br>
<br>
<br>

## 레스트 (나머지)
- 스프레드의 반대 기능 
- 뒤에 남는 것들을 받아줌
```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
const [zero, ...rest] = numbers;
console.log(rest);  // [1, 2, 3, 4, 5, 6]
```

<br>
<br>
<br>

# 나만의 클라이언트 앱 만들기

## 프로젝트 간단 설명
- 나만의 개발자 유형 테스트 만들기
- Main > QnA > Result
- SPA (Single Page Application)
    - 서버로부터 완전한 페이지를 불러오지 않고 현재 페이지를 동적으로 다시 작성함으로써 사용자와 소통하는 웹 애플리케이션이나 웹 사이트

## 프로젝트 코딩하기

### 1. Main
- Main_title / Box / Main_image / Main_intro / Main_startBtn
- 3개 섹션 중 qna, result 부분은 display: none으로 설정
- bootstrap 사용해서 꾸미기
```css
#qna {
    display: none;
}

#result {
    display: none;
}
```
- 버튼을 누르면 다음 페이지로 넘어가기
```js
const main = document.querySelector("#main");
const qna = documnet.querySelector("#qna");

function start() {
    main.style.display = "none";
    qna.style.display = "block";
}
```

<br>

### 2. QnA
- QnA_status / QnA_q / QnA_a
- 각각의 질문과 대답들이 리스트 형태로 
    - 대답들에는 타입들이 존재
```js
const qnaList = [
    {
        q: '친구가 쿠키를 만들었다며 나누어준다. 고마움과 동시에 당신은 어떤 생각을 하게 되는가?',
        a: [
            {answer: 'a. 어떤 비율과 레시피로 만들었길래 이렇게 맛있지?', type: [0, 1]},
            {answer: 'b. 쿠키 모양이 너무 예뻐서 못먹겠다', type: [2, 1]},
            {answer: 'c. 베이킹 사업을 같이 하자고 제안해봐야겠어', type: [0, 3]},
        ]
    },
    {
        q: 'blahblah',
        a: [
            {answer: 'blahblah', type: [1, 2, 3]},
            {answer: 'blahblah', type: [0]},
            {answer: 'blahblah', type: [3]},
        ]
    },
    ...
]
```
```html
<section id="qna">
    <div class="qBox"></div>
    <div class="aBox"></div>
</section>
```
```js
function addAnswer(answerText, qIdx, idx) {
    var a = document.querySelector('.aBox');
    var answer = document.createElement('button');

    a.appendChild(answer);
    answer.innerHTML = answerText;

    answer.addEventListener("click", function(){
        var children = document.querySelectorAll('.answerList');
        for (let i = 0; i < children.length; i++) {
            children[i].disabled = true;  // 버튼 비활성화

            children[i].style.WebkitAnimation = "fadeOut 0.5s";  
            children[i].style.animation = "fadeOut 0.5s";
        }
        setTimeout(() => {
            for(let i = 0; i < children.length; i++){
                children[i].style.display = 'none';  // 버튼 사라짐
            }
            goNext(++qIdx);
        }, 450)
    }, false)
}

function goNext(qIdx){
    var q = document.querySelector('.qbox');
    q.innerHTML = qna(qIdx).q;

    for(let i in qnaList(qIdx).a) {
        addAnswer(qnaList[qIdx].a[i].answer, qIdx, i);
    }
}

function start() {
    ...

    let qIdx = 0;
    goNext(qIdx);
}
```

<br>

- 상태바 만들기
```html
<section id="qna">
    <!-- 추가 -->
    <div class="status">  
        <div class="countStatus"></div>
        <div class="statusBar"></div>
    </div>

    <div class="qBox"></div>
    <div class="aBox"></div>
</section>
```
```js
const endPoint = 10;

function goNext(qIdx) {
    ...

    // 진행현황 숫자
    var countStatusNum = document.querySelector('.countStatus');
    constStatusNum.innerHTML = (qIdx + 1) + "/" + endPoint;

    // 상태바
    var status = document.querySelector('.statusBar');
    status.style.width = (100 / endPoint) * (qIdx + 1) + "%";
}
```

<br>

### 3. result
- 백엔드 : 0, 프론트 : 1, 디자인 : 2, 기획 : 3
- 숫자가 제일 많은 것이 result
```js
const infoList = [
    {
        nameIntro: "뒤에서 묵묵히 해낼게!";
        name: '<백엔드형>',
        descTitle1: 'blahblah',
        desc1: 'blablah',
        descTitle2: 'blahblah',
        desc2: 'blahblah',
        resultif: 'blahblah',
        resultbasic1: 'blahblah',
        resultbasic2: 'blahblah',
        resultbasic3: 'blahblah',
    },
    {
        ...
    },
    ...
]
```
```js
const select = [0, 0, 0, 0];  // 선택된 값 계산
const result = document.querySelector("#result");

function addAnswer(answerText, qIdx, idx) {
    ...

    setTimeOut(() => {
        var target = qnaList[qIdx].a[idx].type;

        for(let i = 0; i < target.length; i++){
            select[target[i]] += 1
        }

        ...
    })
}

function calResult() {
    var result = select.indexOf(Math.max(...select));
    return result;
}

function setResult() {
    let point = calResult();

    // infoList에서 값 가져오기
    const resultNameIntro = document.querySelector('.resultIntro');
    resultNameIntro.innerHTML = infoList(point).nameIntro;

    const resultName = document.querySelector('.resultName');
    resultName.innerHTML = infoList(point).name;

    var resultImg = document.querySelector('.resultImg');
    const imgDiv = document.querySelector("#resultImg");
    var imgURL = "img/image-" + point + ".png";

    resultImg.src = imgURL;
    resultImg.alt = point;
    resultImg.classList.add('img-fluid');
    imgDiv.appendChild(resultImg);

    // 다른 디스크립션도 위와 똑같이 작성
}

function goResult() {
    qna.style.WebkitAnimation = 'fadeOut 1s';
    qna.style.animation = 'fadeOut 1s';

    setTimeOut(() => {
        result.style.WebkitAnimation = 'fadeIn 1s';
        result.style.animation = 'fadeIn 1s';
        setTimeout(() => {
            qna.style.display = 'none';
            result.style.display = 'block';
        }, 450);
    }, 450);

    setResult();
}

function goNext(qIdx) {
    if(qIdx == endPoint) {
        goResult();
        return;
    }
    ...
}
```
```html
<section id="result">
    <h2>나의 결과는?</h2>
    <div>
        <div class="resultIntro"></div>
        <div class="resultName"></div>
    </div>
    <div class="resultImg"></div>
    <div class="resultDesc">
        <div class="resultDescTitle1"></div>
        <div class="resultDescTitle2"></div>
        <div class="resultDesc1"></div>
    </div>
</section>
```

<br>
<br>
<br>

# 자바스크립트를 통해 DATA fetch 하는 웹 만들기

## 프로젝트 간단 설명
- 데이터를 주고 받는 방법

### 1. 데이터 주고받기의 필요성
- 정적 웹페이지 (정보 전달)는 저장된 정보만 보여주기 때문에 서비스가 한정적
- 더 많은 정보를 효율적으로 보여주거나 블로그나 메신저를 만들고 싶다면? -> 데이터 주고받기
- Django 사용 
    - 웹 브라우저에서 요청 -> 저장되어 있는 정적 파일뿐만 아니라 파이썬으로 짜여진 로직이나 데이터베이스에 저장되어 있는 데이터들을 가공해서 html, css, javascript를 만들어서 웹 브라우저에 전달
- 프론트엔드 서버에서 백엔드 서버에 데이터 요청 -> 이 방법 사용

<br>

### 2. 데이터 주고받기의 방법
- 어떤 방식으로 정보를 주고 받을까?
    - 어떤 원칙을 가지고 프로그램 사이를 연결할 것인가? : API
    - 프론트엔드와 백엔드 서버 사이에 API 사용
    - API는 REST 사용
- REST API는 어떤 원칙을 가지고 있을까?
    - URI는 정보의 자원을 표현해야 한다
        - GET/members/delete/1 (x)
        - DELETE/memebers/1 (o)
    - 자원에 대한 행위는 HTTP Method (GET, POST, PUT, DELETE)로 표현한다
        - GET/members/insert/2 (x)
        - POST/members/2 (o)
- REST METHOD
    - POST : POST를 통해 해당 URP를 요청하면 리소스를 생성한다.
    - GET : GET를 통해 해당 리소스를 조회한다. 리소스를 조회하고 해당 도큐먼트에 대한 자세한 정보를 가져온다.
    - PUT : PUT를 통해 해당 리소스를 수정한다.
    - DELETE : DELETE를 통해 리소스를 삭제한다.
- 정보의 형태는 어떻게 할까? -> XML, JSON
    - JSON (Javascript Object Notation) : 단순히 data format / 프로그래밍 언어에 독립적

<br>

### 3. 자바스크립트로 REST API 활용
- Fetch : JS의 내장 라이브러리, IE 지원 X, 일부 기능 부족
- Axios : 외부 라이브러리 모듈 설치 필요, 크로스 브라우징 가능, Response timeout 처리 등 다양한 기능 존재

<br>

### 4. 영화 API 실습
- 영화의 목록을 보여주는 웹사이트
- 정적 사이트라면 데이터를 계속 업데이트 해줘야 함 
- 백엔드 서버에서 데이터만 최신화
- TMDB : 영화 외부 API (백엔드 서버)
