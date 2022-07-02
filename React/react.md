![KakaoTalk_20220702_222455214](https://user-images.githubusercontent.com/83055813/177002790-a49f297a-881f-4f1e-9ad2-e3e0e9b693db.png)

<br>

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

<br>

## useEffect()
- 리액트 컴포넌트가 렌더링 될 때마다 특정 작업을 실행할 수 있도록 하는 Hook
- 형태 : useEffect(function, deps)
    - function : 수행하고자 하는 작업
    - deps : 검사하고자 하는 값 또는 배열
- 가장 처음 렌더링 될 때 한번만 실행 : 빈 배열 넣기
    - useEffect(function, [])
- 특정 props나 state가 바뀔 때 실행 : 특정 값 넣기
    - useEffect(function, [바뀌는 값])

<br>

## useMemo()
- 성능 최적화를 위해 연산된 값을 재사용하게 해주는 Hook
- 형태 : useMemo(function, deps)
    - function : 어떤 연산을 할 지 정의하는 함수
    - deps : 검사하고자 하는 값 또는 배열
- 특정 값이 바뀌면 함수를 호출하여 연산하고, 값이 바뀌지 않으면 재사용
    - useMemo(function, [특정값])

<br>

## React에서 form 다루기

### 1. 일반적인 <form>의 방식
```html
<form>
    <input type="text" name="id" />
</form>
```
- input창에 id 값을 입력하면 id = 입력한 id 값

<br>

### 2. 제어 컴포넌트 (Controlled Component)
- React에서 폼(<input>, <textarea>, <select>)에 발생하는 사용자 입력값을 제어하는 방식

<br>
<br>
<br>

# 리액트 라우터

## MPA
- Multiple Page Application : 여러개의 페이지로 구성된 웹 어플리케이션
- 사용자가 새로운 페이지를 요청할때마다 서버에서 미리 준비한 화면을 보여줌
- 단점
    - 페이지를 이동하거나 새로고침할때 전체 페이지를 다시 렌더링하기 때문에 상태 유지가 어렵고 불필요한 로딩이 발생

<br>

## SPA
- Single Page Application : 한개의 페이지로 구성된 웹 어플리케이션
- 페이지 이동 시 기존 페이지를 수정해서 보여줌

<br>

### 1. 라우팅
- 다른 주소에 다른 화면을 보여주는 것

<br>

### 2. 리액트 라우터
- 사용방법
    - 리액트 프로젝트 생성 및 리액트 라우터 라이브러리 설치
    - 리액트 프로젝트에 라우터 적용하기
    - 페이지 컴포넌트 만들어주기
    - Route 컴포넌트로 특정 주소에 컴포넌트 연결하기
    - Navbar 만들고 Link 컴포넌트로 다른 페이지 이동하기
    - Navbar를 페이지들의 공통 레이아웃 컴포넌트로 만들기
    - URL 파라미터 사용하기
    - 쿼리 스트링 사용하기
    - 리액트 라우터 부가기능 사용하기

<br>

#### 1. 리액트 프로젝트 생성 및 리액트 라우터 라이브러리 설치
```
> yarn create react-app '프로젝트명'
```
``` 
<!-- 프로젝트 파일 안에서 -->
> npm install react-router-dom@6
```
```js
// index.js
import { BrowserRouter } from "react-router-dom";

root.render(
    <React.StrictMode>
        <BrowserRouter>
            <App />
        </BrowserRouter>
    </React.StrictMode>
);
```
- <App />을 <BrowerRouter>로 감싸줌
- 라우터를 이용해 특정 주소의 컴포넌트를 연결
- 페이지들 생성
    - src > pages 폴더 생성 후 페이지 생성
    - rsc 입력 (! + tab 과 동일)

<br>

#### 2. 리액트 페이지에 라우터 적용하기
- Route 사용법
```jsx
<Route path="주소규칙" element={보여 줄 컴포넌트}/>
```
- App.js 내용 모두 삭제 -> 함수형 컴포넌트 구조로 새로 생성 (rsc)
```js
//  App.js
import React from "react";
import { Routes, Route } from "react-router-dom";
import Home from "./pages/Home";  // 생성한 페이지
import Movies from "./pages/Movies";  // 생성한 페이지

const App = () => {
    return (
        <Routes>
            <Route path="/" element={<Home />}></Route>  // localhost:3000
            <Route path="/movies" element={<Movies />}></Route>  // localhost:3000/movies
        </Routes>
    );
};

export default App;
```

<br>

#### 3. Navbar 만들고 Link 컴포넌트로 다른 페이지 이동하기
- pages 폴더에 'Menubar.js" 생성 후 App.js에 컴포넌트 import하고 주소 생성
- 메뉴바를 누르면 해당 컴포넌트로 이동
    - 리액트 라우터의 Link 태그 사용 (페이지 전환을 방지하는 기능 탑재)
- Link 사용법
```jsx
<Link to="주소"></Link>
```
```js
// Menubar.js
import React from "react";
import { Link } from "react-router-dom";

const Menubar = () => {
    return (
        <div>
            <ul>
                <li>
                    <Link to="/home">Home</Link>
                </li>
                <li>
                    <Link to="/movies">Movies</Link>
                </li>
            </ul>
        </div>
    );
};

export default Menubar;
```

<br>

#### 4. Navbar를 페이지들의 공통 레이아웃 컴포넌트로 만들기
- 라우터의 중첩 경로 이용
```js
// App.js
const App = () => {
    return (
        <Routes>
            <Route path="/" element={<Menubar />}>  // 중첩 경로 
                <Route path="/home" element={<Home />}></Route>
                <Route path="/movies" element={<Movies />}></Route>  
            </Route>
        </Routes>
    );
};
```
- 위 처럼 하면 상위, 하위 경로 모두 상위 요소만 보이게 됨 -> 아울렛이라는 컴포넌트 사용해서 해결
```js
// Menubar.js
import { Link, Outlet } from "react-router-dom";

const Menubar = () => {
    return (
        <div>
            <ul>
                <li>
                    <Link to="/home">Home</Link>
                </li>
                <li>
                    <Link to="/movies">Movies</Link>
                </li>
            </ul>

            <Outlet />
        </div>
    );
};
```

<br>

#### 5. 페이지 주소 정의
- URL 파리미터 예시 : /movies/1
    - 특정 아이디, 이름을 사용하여 조회할 때 사용
- 쿼리스트링 예시 : /movies/1?detail=true
    - 키워드 검색, 페이지네이션, 옵션 전달

<br>

#### 6. URL 파라미터 사용하기
- src > movie_data.js 데이터 파일 생성
- 만들어준 영화 데이터들을 movies 컴포넌트 안에 map 함수를 사용하여 보여줌
- src > Movie.js 파일 생성 (rsc)
```js
// App.js
import Movie from "./pages/Miovie";

const App = () => {
    return (
        <Routes>
            <Route path="/" element={<Menubar />}>  
                <Route path="/home" element={<Home />}></Route>
                <Route path="/movies" element={<Movies />}>
                    <Route path=":movieId" element={<Movie />}>  
                </Route>  
            </Route>
        </Routes>
    );
};
```
```js
// movie_data.js
let movies = [
    {
        id: 1,
        title: "하울의 움직이는 성",
        director: "미야자키 하야오",
        category: "일본 애니메이션",
        detail:
            "어느 날, 영문도 모른 채 마녀의 저주로 인해 할머니가 된 소녀 '소피' 절망 속에서 길을 걷다가 거대한 마법의 성에 들어가게 된다. 그곳에서 자신과 마법사 하울의 계약을 깨주면 저주를 풀어주겠다는 불꽃악마 캘시퍼의 제안을 받고 청소부가 되어 ‘움직이는 성’에 머물게 되는데…"
    },
    {
        id: 2,
        title: "보스 베이비2",
        director: "톰 맥그라스",
        category: "미국 애니메이션",
        detail:
            "베이비 주식회사의 레전드 보스 베이비에서 인생 만렙 CEO가 된 ‘테드’. 베이비인 줄 알았던 조카 ‘티나’가 알고 보니 베이비 주식회사 소속 임원으로 밝혀진다. 뉴 보스 베이비 ‘티나’의 지시로 다시 베이비로 돌아간 ‘테드’와 형 ‘팀’에게 주어진 시간은 48시간! 세상을 구하기 위한 미션을 무사히 완수할 수 있을 것인가?"
    },

    ...
];

// 전체 영화 목록이 반환되게 하는 함수
export function getMovies() {  
    return movies;
}

// id로 하나의 영화 정보만 가져오게 하는 함수
export function getMovie(id) {
    return movies.find((movie) => movie.id === id);
}
```
```js
// Movies.js
import React from "react";
import { getMovies } from "../movie_data";
import { Link, Outlet } from "react-router-dom";

const moives = () => {
    const movies = getMovies();  // movies 안에 영화 목록 저장

    return (
        <div>
            <h1>넷플릭스 영화 추천 목록</h1>
            <div>
                {movies.map((movie) => (
                    <Link 
                    to={`/movies/${movie.id}`}
                    key={movie.id}
                    style={{display: "block"}}>
                        <p>{movie.title}</p>
                    </Link>
                ))}
            </div>
            <hr />
            <Outlet />
        </div>
    );
};

export default movies;
```
- 영화 제목을 클릭하면 상세페이지로 이동
- url 파라미터는 use params 사용해 객체 형태로 조회 가능
```js
// Movie.js
import React from "react";
import { useParams } from "react-router-dom";
import { getMovie } from "../movie_data";

const Movie = () => {
    // url 파라미터 사용하기
    const params = useParams();
    const movie = getMovie(parseInt(params.movieId));  // 문쟈형태이기 때문에 숫자로 변환

    return (
        <div>
            <h2>{movie.title}</h2>
            <p>감독 : {movie.director}</p>
            <p>카테고리 : {movie.category}</p>
        </div>
    );
};

export default Movie
```

<br>

#### 7. 쿼리 스트링 사용하기
- 페이지 정보를 알기 위해 useLocation 사용
- 쿼리 스트링은 라우터 컴포넌트를 별도로 설정하지 않아도 됨
- 쿼리 스트링은 useLocation의 search 값을 통해 조회 가능
- 조회한 쿼리 스트링을 파싱하여 자세히 버튼을 눌렀을 때 detail 값 true로, 한번 더 누르면 false 값으로
    - 쿼리 스트링을 파싱할 때는 'useSearchParams' 사용
    - useSearchParams의 get 메서드는 쿼리 파라미터 조회
    - useSearchParams의 set 메서드는 특정 쿼리 파라미터를 업데이트
```js
//  Movie.js
import { useParams, useLocation, useSearchParams } from "react-router-dom";
...

const Movie = () => {
    ...

    // 쿼리 스트링 사용하기
    const location = useLocation();  
    console.log(location);  // pathname, search, hash, state, key 값 출력

    const [searchParams, setSearchParams] = useSearchParams();
    console.log(searchParmas.get("detail"));  // true
    const detail = searchParams.get("detail");

    // 클릭 이벤트 발생했을 때 true -> false, false -> true
    const handleClick = () => {
        setSearchParams({detail: detail === "true" ? false: true});
    }

    return (
        <div>
            <h2>{movie.title}</h2>
            <p>감독 : {movie.director}</p>
            <p>카테고리 : {movie.category}</p>
            <button type="button" onClick={handleClick}>자세히</button>
            {detail === "true" ? <p>{movie.detail}</p> : " "}  // detail의 true는 문자열
        </div>
    );
};
```

<br>

#### 8. NotFound 페이지 만들기
```js
// App.js
const App = () => {
    return (
        <Routes>
            <Route path="/" element={<Menubar />}>  
                <Route path="/home" element={<Home />}></Route>
                <Route path="/movies" element={<Movies />}>
                    <Route path=":movieId" element={<Movie />}>  
                </Route>
                <Route path="*" element={<div>There's nothing here!</div>} />  // NotFound
            </Route>
        </Routes>
    );
};
```

<br>

#### 9. Navigate 컴포넌트
- 페이지 이동할 때 사용
- 홈으로 돌아가는 버튼
```js
// Menubar.js
import { Link, Outlet, useNavigate } from "react-router-dom";

const Menubar = () => {
    // 홈으로 돌아가기 버튼 누를 때
    const navigate = useNavigate();
    const goHome = () => {
        navigate("/");
    };

    return (
        <div>
            <ul>
                <li>
                    <Link to="/home">Home</Link>
                </li>
                <li>
                    <Link to="/movies">Movies</Link>
                </li>
            </ul>

            <Outlet />

            <button type="button" onClick={goHome}>홈으로 돌아가기</button>
        </div>
    );
};
```

<br>

#### 10. NavLink
- Link 대신 NavLink를 사용하면 Link에서 사용하는 경로가 현재 라우터의 경로와 일치하는 경우 특정 css를 적용할 수 있음
- 선택된 리스트에 스타일 적용
```js
// Movies.js
import { NavLink, Link, Outlet } from "react-router-dom";

...

return (
    ...
    // Link -> NavLink
    <NavLink
    to={`/movies/${movie.id}`}
    key={movie.id}
    style={({isActive}) => {
        return {
            textDecoration: isActive ? "underline" : "",
            color: isActive ? "#FF9E1B" : "",
        };
    }}>
        <p>{movie.title}</p>     
    </NavLink>
)
```

<br>
<br>
<br>

# virtual DOM, useRef, useCallback, React.memo

## virtual DOM
- 기존의 DOM이 웹 화면을 보여주는 방식
    - DOM tree 생성 : HTML을 파싱하여 DOM 노드로 이뤄진 트리 생성
    - Render tree 생성 : CSS를 파싱하여 CSSOM 생성 / DOM + CSSOM = Render tree
    - Layout : Render tree 노드들의 위치 결정
    - Paint : 그려서 보여주기
- 기존 DOM의 문제
    - 변화가 생길때마다, 다시 tree를 전부 생성
    - spa를 많이 사용함에 따라 효율적인 DOM 변화의 필요성이 부각 
- virtual DOM 
    - Real DOM의 추상화 버전
    - 비슷한 역할을 하지만 다른 사용방법
    - State가 change되는 상태일 때는 change를 반영하지 않음
    - Diff 알고리즘을 통해서 어떤 부분이 달라졌는 지 확인
    - 전과 비교해서 달라진 부분만 바꿔서 Re-render

<br>

### 1. Virtual DOM의 동작 방식
- Props를 변화시키거나 setState를 사용하여 변화시키는 경우
    - component는 re-render
- 메모리에서 변화 부분 감지 -> 달라진 부분 적용

<br>

## useRef
- Real DOM을 조작할 때 사용했던 getElementById, getElementByClassName 등은 useRef로 사용
    - Real DOM 생성 시에 class name, id 등을 확실히 가져올 보장이 없기 때문에
    - 해당 컴포넌트 안에서만 조작이 가능하여 data flow가 단방향 유지하기 어려움
    - virtual dom에서 조작하고 결과물만 real dom으로 => useRef

### 1. useRef 사용법
- useRef import
```js
import React, { useState, useRef, useEffect } from "react";
```
- useRef 할당
```js
function InputPost({ onChange, title, contents }) {
    const titleInput = useRef();
    const contentInput = useRef();
}
```
- useRef 연결
```js
<TitleInput 
    ...
    ref={titleInput}/>
```
- useRef 사용
```js
const onKeyUp = (e) => {
    if (e.key === "Enter") {
        contentsInput.current.focus();
    }
};

useEffect(() => {
    titleInput.current.focus();
}, []);
```

<br>

## useCallback
- 최적화
- 컴포넌트가 리랜더될 때마다 컴포넌트의 함수가 재생성된다
- useCallback은 어떤 부분을 미리 memorize해서 필요할 때 꺼내쓴다
- 연산이 오래 걸리고 복잡한 함수일수록 해당 과정이 더욱 효율적

### 1. useCallback 사용법
- useCallback import
```js
import React, { useState, useEffect, useCallback } from 'react';
```
- 해당 함수를 useCallback 함수로 감싸기
```js
const addPost = useCallback(() => {
    setPostList((postList) => [
        ...postList,
        { id: 4, title: "학보, 시사n 대학기자상 취재" },
    ]);
}, [postList]);
```
- [postList] : Deps(dependency array)에 있는 부분이 바뀌면 다시 만들기

<br>

## React.memo
- Props가 안 바뀌어도, setState로 변화가 일어나지 않아도 상위 컴포넌트가 re-render 되면 재귀적으로 re-render되는 경우가 있음
- 컴포넌트를 memorize 해놨다가 정말 필요한 상황에서만 re-render => React.memo

### 1. React.memo 사용법
- React.memo import
```js
import React, { useState, useEffect, useCallback } from "react";
```
- 기존 컴포넌트를 react.memo로 감싸거나 export 부분을 react.memo로 감싸기
```js
// 둘 중 하나 택 1
const SubmitComponent : React.memo{() => (
    <PostSubmitDiv>
        <postSubmit>작성완료</postSubmit>
    </PostSubmitDiv>
)};

export default React.memo(WriteTitle);
```
