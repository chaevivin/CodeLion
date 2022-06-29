# 리액트 기초

## 리액트란?
- 유저 인터페이스를 만들기 위한 자바스크립트 라이브러리
- 리액트는 facebook에서 만든 오픈소스 라이브러리
- UI (User Interface) : 사용자가 경험을 할 때 직접 상호 작용하는 부분
    - 컴퓨터와 모니터와 마우스, 화면, 메뉴바, 버튼 등
- 라이브러리 : 불러와 사용하는 도구

<br>

## 리액트 환경 세팅
- node js 설치
- npm, yarn 설치
    - npm(node package manager) : 자바스크립트 라이브러리들을 설치하고 버전을 관리
    - yarn : facebook에서 npm의 단점을 보완한 라이브러리 관리 도구

<br>

### 1. 리액트 앱 생성하기
- >yarn create react-app '프로젝트명'
- >yarn start
- >cd react-study
- >yarn start

```jsx
// Hello.jsx
import React from "react";

function Hello(){
    return <div>Hello World!</div>
}
export default Hello;
```
```js
// App.js
import Hello from "./Hello";

function App() {
  return (
    <Hello/>
  );
}

export default App;
```

<br>

### 2. 리액트 extension
- 크롬
    - react developer tools : react element 구조 쉽게 파악 가능
- VScode
    - reactjs code snippets : rfc만 치면 기본 구조 나옴
    - Auto Import - ES6, TS, JSX, TSX

<br>
<br>
<br>

# JSX

## JSX란?
- JS + XML
    - XML(EXtensionable Markup Language) : 데이터를 저장하고 전달하는 것이 목표
- Babel : JSX를 JS로 변환
    - JSX : 선언형 (결과물을 선언)
    - JS : 명령형 (어떻게 만들지 방법을 명령)

<br>

## JSX 문법

### 1. 하나의 요소로 감싼다
- <div> 태그 보다는 <Fragment> 태그로 감싸기
- <Fragment>, </Fragment> -> <>, </>
```js 
function App() {
    const name = "chaebin";
    return (
        <div>
            <Hello/>
            <div>Nice to meet you!</div>
        </div>
    );
}
function Hello() {
    return (
        <Fragment>
            <div>Hello</div>
            <div>I'm chaebin!</div>
        </Fragment>
    );
}

↓

<div>
    <div>Hello</div>
    <div>I'm chaebin!</div>
    <div>Nice to meet you!</div>
</div>
```

<br>

### 2. 자바스크립트 표현식의 사용
- {} 로 감싸기
```js
functon Hello() {
    const name = "chaebin";
    return (
        <>
            <div>Hello</div>
            <div>I'm {name}!</div>
        </>
    );
}

↓

<div>Hello</div>
<div>I'm chaebin!</div>
```

<br>

### 3. 조건부 렌더링
- jsx안에서 if, for문 사용 불가
- 해결 방법
    - Return문 밖에서 if문 사용
    - &&와 || 이용
    - Switch, Case문 사용
    - 삼항연산자 (중첩 사용 가능) 
    
```js
// Return문 밖에서 사용
function App() {
    const num = 1;
    if(num == 1) {
        return <>num is 1</>
    }
    return <>num is not 1</>
}

// &&, ||
function App() {
    const num = 1;
    return (
        <>
            {num == 1 && <div>num은 1이 맞습니다.</div>}  // 왼쪽이 참일때만 오른쪽 값 렌더링 
            {num == 1 || <div>num은 1이 아닙니다.</div>}  // 왼쪽이 거짓일때만 오른쪽 값 렌더링
        </div>
    );
}

// switch-case
function App(){
    const status = "happy";
    switch(status) {
        case "happy":
            return <p>좋은 아침!</p>
        case "angry":
            return <p>열불나</p>
        default:
            return <p>안녕하세요</p>
    }
}

// 삼항연산자
function App() {
    const num = 1;
    return (
        <>
            {
                num === 1
                ?<div>num은 1이 맞습니다.</div>
                :<div>num은 1이 아닙니다.</div>
            }
        </>
    );
}
```

<br>

## Style basic

### 1. inline
- 1. css의 속성을 모두 camel case로 작성해야 함
- 2. style을 미리 선언하여 사용 가능
- 3. 기존의 css 파일 적용해서 사용
```jsx
// 1
import React from "react";

function Hello(){
    return <div style={{ marginTop: '10px', backgroundColor: 'red' }}>Hello World!</div>
}
export default Hello;
```
```jsx
// 2
import React from "react";

function Hello(){
    const PracticeStyle = {
        marginTop: '10px',
        backgroundColor: 'blue',
    };
    return (
        <>
            <div style={PracticeStyle}>Hello World!</div>
            <div style={PracticeStyle}>Hello World!</div>
            <div style={PracticeStyle}>Hello World!</div>
        </>
    )
}
export default Hello;
```
```jsx
// 3
import React from "react";
import "./Hello.css";

function Hello(){
    return (
        <>
            <div className="red">Hello World!</div>
            <div className="red">Hello World!</div>
            <div className="red">Hello World!</div>
        </>
    )
}
export default Hello;
```
```css
.red {
    background-color: red;
    color: beige;
    font-size: 48px;
    padding: 16px;
}
```

<br>

### 2. Styled Componets
- JS안에 CSS를 작성할 수 있는 라이브러리
- 설치
    - >yarn add styled-components
    - 설치 완료 : package.json에 styled-components 추가
- 사용
    - import로 불러오기
    - react에서 component 이름은 무조건 대문자!
    - StyledButton에 저장되는 것은 react component
```jsx
import React from "react";
import styled from "styled-components";

function Hello(){
    const StyledButton = styled.button`
        color:red;
        background-colo:gray;
    `
    return (
        <StyledButton>버튼</StyledButton>
    )
}
export default Hello;
```

<br>

## 실습
- 익명 게시판 만들기

### 실습 목표 정리
- Dark Mode
    - Dark  Mode와 Light Mdoe 조건부 렌더링 UI를 구현한다
- Loading
    - Loading True : 로딩중일 경우 로딩 이미지를 표시
    - Loading False : 게시글을 표시
    - Loading False && No Post : 로딩이 끝났지만 표시 할 포스트가 없을 경우 없다는 문구를 띄워준다.

<br>
<br>
<br>

# State & Component 사용하기 

<br>

## Component

### 1. Component란?
- 앱을 이루는 최소한의 단위
- UI는 재사용 가능한 개별적인 여러 조각으로 나누고 각 조각을 개별적으로 나누어 코딩
- props 혹은 state 값을 입력 받아 DOM 노드 생성
- 이름은 항상 대문자
    - 소문자로 시작하는 컴포넌트는 DOM 태그로 취급

<br>

### 2. Component의 선언 방식
- 클래스형과 함수형
- 리액트 매뉴얼에서 권고하는 방식은 함수형 + Hooks
- 클래스형 컴포넌트
    - state 기능, 라이프 사이클 기능을 내부적으로 제공
    - 사용자가 임의 메서드 정의 가능
    - 컴포넌트 내부에 render 함수 필수 : render 함수 내부에서 jsx 반환
- 함수형 컴포넌트
    - state, 라이프사이클 api 사용 불가능 : 16.8 업데이트 이후 Hooks 도입으로 해결
    - 배포 단계에서도 비교적 작은 파일 크기
    - 편한 선언, 비교적 적은 메모리 자원 사용
```jsx
// 클래스형
class App extends Component {
    render() {
        return
            <h1>likelion</h1>
    }
}

// 함수형
function App() {
    return
        <h1>likelion</h1>
}
```

<br>

## Props

### 1. Props란?
- properties
- 컴포넌트 속성 설정 시에 사용하는 요소
- props의 값은 부모 컴포넌트에서 설정해준다.
- 자식 컴포넌트를 수정하여 렌더링

<br>

### 2. defaultProps
- 별도의 props 값이 없는 경우 보여주는 기본 값
```js
MyComponent.defaultProps = {
    grade: "default",
};
```

<br>

### 3. 더 짧은 코드 사용하기
- 비구조화 할당 문법으로 내부 값 추출
```js
import React from "react";

function MyComponent({ grade }) {
    return (
        <div>
            {grade} 아기 사자 여러분 반갑습니다!
        </div>
    );
}

export default MyComponent;
```

<br>

## State

### 1. State란?
- 컴포넌트 내부에서 바뀔 수 있는 값
- 함수형 컴포넌트 -> useState라는 함수를 통해 사용
- 클래스형 컴포넌트 -> 지니고 있는 state

<br>

### 2. useState
- 배열의 비구조화 할당
    - 배열 안에 들어 있는 값을 쉽게 추출할 수 있는 문법
```js
// console.log(one);  console.log(two);
// 두 코드의 결과 동일
const array = [1, 2];
const one = array[0];
const two = array[1];

const array1 = [1, 2];
const [one, two] = array1;
```
- 함수형 컴포넌트에서 state 사용하기 -> 내장 Hooks
    - 아래와 같이 작성하며 배열에 첫 번째 원소에는 현재 상태 저장
    - 배열에 두 번째 원소에는 상태를 바꿔주는 setter 함수
    - 함수 인자에는 상태의 초기값
```js
const [message, setMessage] = useState("초기값");
```

<br>

### 3. props와 state
- props
    - 부모 컴포넌트로부터 자녀 컴포넌트에 데이터 등을 전달
    - 읽기 전용으로 자녀 컴포넌트 입장에서 변동 없음
- state 
    - 해당 컴포넌트 내부에서 데이터 전달
    - 변경 가능함 : 변경 시 re-render
- Props와 state 모두 컴포넌트에서 사용하거나 렌더링할 데이터를 담고 있어 비슷해 보일 수 있지만 역할은 다르다.

<br>

## Component를 효율적으로 사용하는 방법

### 1. Component 분리
- 재사용 가능한 개별적인 여러 조각으로 나누기
- 모듈(분리한 컴포넌트)를 내보내기 (export)
```js
// 두 방식의 기능은 동일
import React from "react";

export default function MyConmponent() {
    return <div>나의 새롭고 멋진 컴포넌트</div>;
}

// --------------------------------------

import React from "react";

function MyComponent() {
    return <div>나의 새롭고 멋진 컴포넌트</div>;
}

export default MyComponent;
```
- 모듈(분리한 컴포넌트)를 불러오기 (import)
```js
import React from "react";
import MyComponent from "./MyComponent";
// 만든 컴포넌트 불러오기

const App = () => {
    return (
        <div>
            <MyComponent />
            <div>import 했습니다.</div>
        </div>
    );
};

export default App;
```

<br>

### 2. Component의 반복
- Map() 함수
    - 반복되는 형태의 코드를 효율적으로 보여주고 관리하는 방법
    - 파라미터로 전달된 함수로 배열 내 각 요소를 원하는 규칙에 따라 변환해 그 결과로 새로운 배열 생성
    ```js
    arr.map(callbackFunction(currentValue, index, array), [thisArg])
    ```
    - callbackFunction : 새로운 배열 요소를 처리하는 함수
    - currentValue : 현재 처리하고 있는 요소
    - Index : 현재 처리하고 있는 요소의 index 값
    - array : 현재 처리하고 있는 원본 배열
    - thisArg : callback 함수 내부에서 사용할 this 레퍼런스
- 배열의 각 요소를 제곱한 새로운 배열 만들기
    ```js
    const numbers = [1, 2, 3, 4, 5];
    const result = numbers.map(num -> num * num);
    console.log(result);  // [1, 4, 9, 16, 25]
    ```
    - numbers : 원본 배열
    - num : 함수의 파라미터
    - num * num : 변환 규칙
- 데이터 배열을 컴포넌트 배열로 변환
    ```js
    import React from "react";

    const IterationSample = () => {
        const names = ['눈사람', '얼음', '눈' '바람'];
        const nameList = names.map(name => <li>{name}</li>);
        return (
            <ul>{nameList}</ul>
        );
    };

    export default IterationSample;
    ```

<br>

### 3. 리액트에서의 key
-  변동된 원소를 알아내기 위함
- key가 없을 때
    - Virtual DOM을 비교하는 과정에서 리스트를 순차적으로 비교하면서 변화 감지
- Key가 있을 때
    - Key 값을 이용하여 변화를 빠르게 알아낼 수 있음
- Key 설정
    - Map 함수의 인자로 전달되는 함수 내부에서 컴포넌트 props를 설정하는 것과 같이 설정
    - Key 값은 언제나 유일
    - 데이터가 가진 고윳값을 key 값으로 설정
    ```js
    const nameList = names.map((name, index) => <li key={index}>{name}</li>);
    ```
