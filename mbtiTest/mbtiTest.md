# 🐆 MBTI TEST : 세렝게티 동물 테스트

## 프로젝트 간단 설명

- 16가지 성격 유형 (MBTI)
- 알파벳 별로 3문제씩 판단 -> 총 12문제
  - 앞쪽 것만 count (e, s, t, j)
- 진행 바, 공유 기능, 광고 (수익화)

<br>

## 프로젝트 코딩하기

### 1. MBTI 원리

- 에너지 방향 : E(외향) / I(내향)
  - E : 넓은 대인관계, 사교적, 정열적, 활동적
  - I : 깊은 대인관계, 조용하고 신중, 이해하고 경험
- 인식 기능 : S(감각) / N(직관)
  - S : 오감에 의존, 실제 경험 중시, 정확한 일처리
  - N : 영감에 의존, 미래지향적, 신속한 일처리
- 판단 기능 : T(사고) / F(감정)
  - T : 진실과 사실 중시, 분석적, 객관적 판단
  - F : 관계에 중심, 상황적 판단
- 생활 양식 : J(판단) / P(인식)
  - J : 분명한 목적과 방향, 기한 엄수
  - P : 상황에 따라 일정 변경, 자율적, 융통성

<br>

### 2. bootstrap, jquery

```html
<head>
  <link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.1/dist/css/bootstrap.min.css"
    integrity="sha384-zCbKRCUGaJDkqS1kPbPd7TveP5iyJE0EjAuZQTgFLD2ylzuqKfdKlfG/eSrtxUkn"
    crossorigin="anonymous"
  />
</head>
<body>
  <script
    src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.slim.min.js"
    integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj"
    crossorigin="anonymous"
  ></script>
  <script
    src="https://cdn.jsdelivr.net/npm/bootstrap@4.6.1/dist/js/bootstrap.bundle.min.js"
    integrity="sha384-fQybjgWLrvvRgtW6bFlB7jaZrFsaBXjsOMm/tB9LTS58ONXgqbR9W8oWht/amnpF"
    crossorigin="anonymous"
  ></script>
</body>
```

<br>

### 3. 첫 번째 시작 페이지

```HTML
<body>
    <h1>나랑 꼭 닮은 세렝게티 동물은?</h>
    <button>테스트 시작하기</button>
</body>
```

- button은 bootstrap 에서 가져다 쓰기 : bootstrap > docs > 검색 창에서 검색

```html
<button>테스트 시작하기</button>
<!-- bootstrap -->
<button type="button" class="btn btn-primary">테스트 시작하기</button>
```

- 간격 띄우기 : bootstrap 클래스 이용
  - body 태그에 container(grid) class 입력
  - h1 태그에 mt-5(margin-top) class 입력해서 위쪽 간격 5만큼 띄우기
  - text-center : 가운데 정렬

```html
<body class="container">
  <h1 class="mt-5 text-center"></h1>
  ...
</body>
```

- 가운데 정렬
  - h1, button 태그 article 태그로 감싸기
  - CSS flex-box 속성 이용

```html
<article class="start">
  <h1>...</h1>
  <button>...</button>
</article>
```

```css
.start {
  display: flex;
  flex-direction: column;
}
```

<br>

### 4. 두 번째 페이지

- 버튼 누르면 화면 전환 (jQuery 이용)
  - button에 onclick 속성
  - jquery로 article 태그 모두 선택 후 숨기기

```html
<button onclick="start();"></button>
<script>
  function start() {
    $(".start").hide();
  }
</script>
```

- 두 번째 페이지 (문제들)
  - 첫 번째 페이지에 그대로 보이기 때문에 두 번째 페이지 내용 가리기

```html
<article class="question">
  <h2>문제</h2>
</article>
```

```css
.question {
  display: none;
}
```

```html
<script>
  function start() {
    $(".question").show();
  }
</script>
```

- 문제 화면 꾸미기
  - progress bar : bootstrap > progress 검색

```html
<div class="progress">
  <div
    class="progress-bar"
    role="progressbar"
    style="width: 25%"
    aria-valuenow="25"
    aria-valuemin="0"
    aria-valuemax="100"
  ></div>
</div>
```

- 대답을 선택할 수 있는 버튼 (bootstrap)
  - 위 아래로 배치 : css .start > article로 변경

```html
<button type="button" class="btn btn-primary">Primary</button>
<button type="button" class="btn btn-primary">Primary</button>
```

- 문제 답을 선택하면 점수로 저장
  - 안 보이게 하면서 저장

```html
<input type="hidden" value="0" />
```

- 버튼을 클릭할때마다 input값 올리기
  - 위의 버튼은 E, S, T, J
  - 아래 버튼은 I, N, F, P
  - type값 가져오기 > 해당하는 input value 값 올려주기

```html
<script>
  $("#A").click(function () {
    const type = $("#type").val(); // type value 가져오기
    const preValue = $("#" + type).val(); // 해당 id 선택
    $("#" + type).val(parseInt(preValue) + 1);
  });
</script>
```

- 버튼을 클릭하면 다음 문제로 넘어가기
  - 문제의 정보들을 JavaScript 객체에 저장
  -

```html
<script>
  let num = 1; // 현재 어떤 문제에 있는지
  const q = {
    // 문제 객체 생성
    1: { title: "문제 1번", type: "EI", A: "E", B: "I" },
    2: { title: "문제 2번", type: "EI", A: "E", B: "I" },
    3: { title: "문제 3번", type: "EI", A: "E", B: "I" },
  };
  function next() {
    // 다음 문제로 넘어가는 함수
    $("#title").html(q[num]["title"]);
    $("#type").val(q[num]["type"]);
    $("#A").html(q[num]["A"]);
    $("#B").html(q[num]["B"]);
    num++;
  }
</script>
```

<br>

### 5. Progress bar

- 총 12문제이므로 1문제를 풀때마다 1/12씩 증가
  - css style 속성 calc() -> 자동으로 수식 계산

```html
<div class="progress mt-5">
  <div
    class="progress-bar"
    role="progressbar"
    style="width: calc(100/12*1%)"
  ></div>
</div>
```

- 문제 클릭할때마다 진행바 증가
  - jquery attr : 태그의 속성 바꿔줌

```html
<script>
  function next() {
    $(".progress-bar").attr("style", "width: calc(100/12*" + num + "%)");
  }
</script>
```

<br>

### 6. 문제 12개 추가하기

- JavaScript q에 객체 12개 생성

<br>

### 7. 마지막 버튼 눌렀을 때 결과 화면

- 결과 화면 생성

```html
<article class="result">
  <img id="img" rc="" alt="" />
  <h2 id="name">동물이름</h2>
  <h3 id="explain">설명</h3>
</article>
```

- 마지막 버튼 눌렀을 때 결과 화면 보여주기

```html
<script>
  function next() {
    if (num == 13) {
      $(".question").hide();
      $(".result").show();
    }
  }
</script>
```

- 결과 화면 꾸며주기
  - pixabay : 무료 이미지

<br>

### 8. 각각 다른 결과 화면이 나올 수 있는 로직 구현

- input의 점수들을 활용해서 결과 계산
- 마지막 문제를 다 풀었을 때 결과값 계산 해야 하기 때문에 next() 함수 안에 구현
- 값이 2 이상이면 앞에 것 (E, S, T, J) / 값이 2 미만이면 뒤에 것 (I, N, F, P) 선택

```html
<script>
  $("#EI").val() < 2 ? (mbti += "I") : (mbti += "E");
  $("#SN").val() < 2 ? (mbti += "N") : (mbti += "S");
  $("#TF").val() < 2 ? (mbti += "F") : (mbti += "T");
  $("#JP").val() < 2 ? (mbti += "P") : (mbti += "J");
</script>
```

<br>

### 9. MBTI에 맞는 동물 
- JavaScript 객체 안에 저장해두었다가 매핑
```html
<script>
    const result = {
        "ISTJ" : {"animal": "하마", "explain": "하마 설명", "img": "lion.jpg"},
        "ENTP" : {"animal": "하마", "explain": "하마 설명", "img": "lion.jpg"},
        "INFJ" : {"animal": "하마", "explain": "하마 설명", "img": "lion.jpg"}
        ...
        }
</script>
```
- 마지막 화면에서 해당하는 값 불러오기
    - img, animal, explain
```html
<script>
    function next() {
        $("#img").attr("src", result[mbti]["img"]);
        $("#animal").html(result[mbti]["animal"]);
        $("#explain").html(result[mbti]["explain"]);
    }
</script>
```

<br>
<br>
<br>

## 배포하기
- netlify 사용
- netlify.com 접속 > 회원가입 > Sites > 작업한 폴더 끌어오기 > 자동 배포
- site 이름 바꾸기 : site settings > change site name 

<br>
<br>
<br>

## SNS 공유 기능 만들기
- AddThis 사용
- addthis.com 접속 > 회원가입 > Share buttons > Select Tool Type으로 원하는 버튼 선택 > continue > sns 표시 선택 > activate tool > script 복사 > body 태그 위에 붙여넣기 > inline에서 div 태그 복사 후 원하는 위치에 붙여넣기

<br>
<br>
<br>

## 광고 붙여서 수익화

### 1. 애드 네트워크 (Google Adsense, KaKao Adfit)
- KaKao Adfit 사용
- KaKao Adfit 접속 > 로그인 > 광고 관리 > 새 매체 > 매체 : 프로젝트 이름, 매체 고유값 : 프로젝트 url > 광고 단위 등록 > 광고 단위 명: (예) 하단 배너1 > 스크립트 sdk 발급 > 코드 복사 > 광고 넣고 싶은 곳에 붙여넣기

<br>

### 2. 직접 광고 계약
- 수수료 없음
- 광고주에게 이미지와 url 제공 받아야 함
```
<!-- 예 -->
https://www.codelion.net/catalog?utm_source=animal_test&utm_medium=web_lecture&utm_campaign=jocoding
```
- utm 코드 : 사이트에 도달하게 되면 어디서부터 왔는지 추적
- utm_campaign : 자신의 id
- 원하는 곳에 광고 부착
```html
<a href="https://www.codelion.net/catalog?utm_source=animal_test&utm_medium=web_lecture&utm_campaign=jocoding">
    <img src="ad.jpg" alt="ad">
</a>
```

<br>
<br>
<br>

## 사이트 검색되도록 만들기

### 1. 네이버 검색에 나오려면?
- 네이버 웹마스터 도구에 내 사이트 등록
- 검색 관련 문서 제출

<br>

### 2. 검색 엔진의 원리
- 크롤러가 인터넷을 돌아다니면서 사이트에 대한 정보를 수집하고 네이버에 저장, 네이버에서 많은 사이트들이 검색되도록 해줌
- robots.txt 라는 문서에 정보 작성 후 크롤링이 가능한지 검사
- sitemap.xml : 크롤러가 크롤링을 잘 할 수 있도록 해줌

<br>

### 3. 네이버 웹마스터 도구에 내 사이트 등록
- searchadvisor.naver.com 접속 > 웹마스터 도구 > 로그인 > 사이트 등록에 url 등록 > 다음 > 사이트 소유 확인 (아무거나 사용) 
- 등록한 사이트 클릭 > 검증 > robots.txt > robots.txt 간단 생성 > 모든 검색 로봇, 수집 허용 > 다운로드 > 다운받은 파일을 작업하던 폴더에 넣어줌 
- 구글에 sitemap generator 검색 > url 입력 > start > 다운로드 > 다운받은 파일을 작업하던 폴더에 넣어줌
- robots.txt, sitemap.xml을 추가한 폴더를 netlify 사이트에서 업데이트 해줌
- 웹마스터 도구 > 수집요청 / 요청 > 사이트맵 제출 > url에 sitemap.xml 입력 > 확인

<br>
<br>
<br>

## 검색엔진 최적화 (SEO)

### 1. SEO란?
- Search Engine Optimization : 검색이 잘 될 수 있도록 최적화
- SEO가 잘 될수록 상단에 배치

<br>

### 2. 검색엔진 최적화하기
- 내부 요소 최적화 (HTML, 컨텐츠, 메타태그 등)
- 외부 요소 최적화 (백링크 개수 등)

<br>

### 3. 최적화 하는 방법
- 네이버 search advisor > 진단하기 > 사이트 간단 체크 > url 입력 > 최적화 상태를 보고 고치기

