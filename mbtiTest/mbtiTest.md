# ๐ MBTI TEST : ์ธ๋ ๊ฒํฐ ๋๋ฌผ ํ์คํธ

## ํ๋ก์ ํธ ๊ฐ๋จ ์ค๋ช

- 16๊ฐ์ง ์ฑ๊ฒฉ ์ ํ (MBTI)
- ์ํ๋ฒณ ๋ณ๋ก 3๋ฌธ์ ์ฉ ํ๋จ -> ์ด 12๋ฌธ์ 
  - ์์ชฝ ๊ฒ๋ง count (e, s, t, j)
- ์งํ ๋ฐ, ๊ณต์  ๊ธฐ๋ฅ, ๊ด๊ณ  (์์ตํ)

<br>

## ํ๋ก์ ํธ ์ฝ๋ฉํ๊ธฐ

### 1. MBTI ์๋ฆฌ

- ์๋์ง ๋ฐฉํฅ : E(์ธํฅ) / I(๋ดํฅ)
  - E : ๋์ ๋์ธ๊ด๊ณ, ์ฌ๊ต์ , ์ ์ด์ , ํ๋์ 
  - I : ๊น์ ๋์ธ๊ด๊ณ, ์กฐ์ฉํ๊ณ  ์ ์ค, ์ดํดํ๊ณ  ๊ฒฝํ
- ์ธ์ ๊ธฐ๋ฅ : S(๊ฐ๊ฐ) / N(์ง๊ด)
  - S : ์ค๊ฐ์ ์์กด, ์ค์  ๊ฒฝํ ์ค์, ์ ํํ ์ผ์ฒ๋ฆฌ
  - N : ์๊ฐ์ ์์กด, ๋ฏธ๋์งํฅ์ , ์ ์ํ ์ผ์ฒ๋ฆฌ
- ํ๋จ ๊ธฐ๋ฅ : T(์ฌ๊ณ ) / F(๊ฐ์ )
  - T : ์ง์ค๊ณผ ์ฌ์ค ์ค์, ๋ถ์์ , ๊ฐ๊ด์  ํ๋จ
  - F : ๊ด๊ณ์ ์ค์ฌ, ์ํฉ์  ํ๋จ
- ์ํ ์์ : J(ํ๋จ) / P(์ธ์)
  - J : ๋ถ๋ชํ ๋ชฉ์ ๊ณผ ๋ฐฉํฅ, ๊ธฐํ ์์
  - P : ์ํฉ์ ๋ฐ๋ผ ์ผ์  ๋ณ๊ฒฝ, ์์จ์ , ์ตํต์ฑ

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

### 3. ์ฒซ ๋ฒ์งธ ์์ ํ์ด์ง

```HTML
<body>
    <h1>๋๋ ๊ผญ ๋ฎ์ ์ธ๋ ๊ฒํฐ ๋๋ฌผ์?</h>
    <button>ํ์คํธ ์์ํ๊ธฐ</button>
</body>
```

- button์ bootstrap ์์ ๊ฐ์ ธ๋ค ์ฐ๊ธฐ : bootstrap > docs > ๊ฒ์ ์ฐฝ์์ ๊ฒ์

```html
<button>ํ์คํธ ์์ํ๊ธฐ</button>
<!-- bootstrap -->
<button type="button" class="btn btn-primary">ํ์คํธ ์์ํ๊ธฐ</button>
```

- ๊ฐ๊ฒฉ ๋์ฐ๊ธฐ : bootstrap ํด๋์ค ์ด์ฉ
  - body ํ๊ทธ์ container(grid) class ์๋ ฅ
  - h1 ํ๊ทธ์ mt-5(margin-top) class ์๋ ฅํด์ ์์ชฝ ๊ฐ๊ฒฉ 5๋งํผ ๋์ฐ๊ธฐ
  - text-center : ๊ฐ์ด๋ฐ ์ ๋ ฌ

```html
<body class="container">
  <h1 class="mt-5 text-center"></h1>
  ...
</body>
```

- ๊ฐ์ด๋ฐ ์ ๋ ฌ
  - h1, button ํ๊ทธ article ํ๊ทธ๋ก ๊ฐ์ธ๊ธฐ
  - CSS flex-box ์์ฑ ์ด์ฉ

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

### 4. ๋ ๋ฒ์งธ ํ์ด์ง

- ๋ฒํผ ๋๋ฅด๋ฉด ํ๋ฉด ์ ํ (jQuery ์ด์ฉ)
  - button์ onclick ์์ฑ
  - jquery๋ก article ํ๊ทธ ๋ชจ๋ ์ ํ ํ ์จ๊ธฐ๊ธฐ

```html
<button onclick="start();"></button>
<script>
  function start() {
    $(".start").hide();
  }
</script>
```

- ๋ ๋ฒ์งธ ํ์ด์ง (๋ฌธ์ ๋ค)
  - ์ฒซ ๋ฒ์งธ ํ์ด์ง์ ๊ทธ๋๋ก ๋ณด์ด๊ธฐ ๋๋ฌธ์ ๋ ๋ฒ์งธ ํ์ด์ง ๋ด์ฉ ๊ฐ๋ฆฌ๊ธฐ

```html
<article class="question">
  <h2>๋ฌธ์ </h2>
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

- ๋ฌธ์  ํ๋ฉด ๊พธ๋ฏธ๊ธฐ
  - progress bar : bootstrap > progress ๊ฒ์

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

- ๋๋ต์ ์ ํํ  ์ ์๋ ๋ฒํผ (bootstrap)
  - ์ ์๋๋ก ๋ฐฐ์น : css .start > article๋ก ๋ณ๊ฒฝ

```html
<button type="button" class="btn btn-primary">Primary</button>
<button type="button" class="btn btn-primary">Primary</button>
```

- ๋ฌธ์  ๋ต์ ์ ํํ๋ฉด ์ ์๋ก ์ ์ฅ
  - ์ ๋ณด์ด๊ฒ ํ๋ฉด์ ์ ์ฅ

```html
<input type="hidden" value="0" />
```

- ๋ฒํผ์ ํด๋ฆญํ ๋๋ง๋ค input๊ฐ ์ฌ๋ฆฌ๊ธฐ
  - ์์ ๋ฒํผ์ E, S, T, J
  - ์๋ ๋ฒํผ์ I, N, F, P
  - type๊ฐ ๊ฐ์ ธ์ค๊ธฐ > ํด๋นํ๋ input value ๊ฐ ์ฌ๋ ค์ฃผ๊ธฐ

```html
<script>
  $("#A").click(function () {
    const type = $("#type").val(); // type value ๊ฐ์ ธ์ค๊ธฐ
    const preValue = $("#" + type).val(); // ํด๋น id ์ ํ
    $("#" + type).val(parseInt(preValue) + 1);
  });
</script>
```

- ๋ฒํผ์ ํด๋ฆญํ๋ฉด ๋ค์ ๋ฌธ์ ๋ก ๋์ด๊ฐ๊ธฐ
  - ๋ฌธ์ ์ ์ ๋ณด๋ค์ JavaScript ๊ฐ์ฒด์ ์ ์ฅ
  -

```html
<script>
  let num = 1; // ํ์ฌ ์ด๋ค ๋ฌธ์ ์ ์๋์ง
  const q = {
    // ๋ฌธ์  ๊ฐ์ฒด ์์ฑ
    1: { title: "๋ฌธ์  1๋ฒ", type: "EI", A: "E", B: "I" },
    2: { title: "๋ฌธ์  2๋ฒ", type: "EI", A: "E", B: "I" },
    3: { title: "๋ฌธ์  3๋ฒ", type: "EI", A: "E", B: "I" },
  };
  function next() {
    // ๋ค์ ๋ฌธ์ ๋ก ๋์ด๊ฐ๋ ํจ์
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

- ์ด 12๋ฌธ์ ์ด๋ฏ๋ก 1๋ฌธ์ ๋ฅผ ํ๋๋ง๋ค 1/12์ฉ ์ฆ๊ฐ
  - css style ์์ฑ calc() -> ์๋์ผ๋ก ์์ ๊ณ์ฐ

```html
<div class="progress mt-5">
  <div
    class="progress-bar"
    role="progressbar"
    style="width: calc(100/12*1%)"
  ></div>
</div>
```

- ๋ฌธ์  ํด๋ฆญํ ๋๋ง๋ค ์งํ๋ฐ ์ฆ๊ฐ
  - jquery attr : ํ๊ทธ์ ์์ฑ ๋ฐ๊ฟ์ค

```html
<script>
  function next() {
    $(".progress-bar").attr("style", "width: calc(100/12*" + num + "%)");
  }
</script>
```

<br>

### 6. ๋ฌธ์  12๊ฐ ์ถ๊ฐํ๊ธฐ

- JavaScript q์ ๊ฐ์ฒด 12๊ฐ ์์ฑ

<br>

### 7. ๋ง์ง๋ง ๋ฒํผ ๋๋ ์ ๋ ๊ฒฐ๊ณผ ํ๋ฉด

- ๊ฒฐ๊ณผ ํ๋ฉด ์์ฑ

```html
<article class="result">
  <img id="img" rc="" alt="" />
  <h2 id="name">๋๋ฌผ์ด๋ฆ</h2>
  <h3 id="explain">์ค๋ช</h3>
</article>
```

- ๋ง์ง๋ง ๋ฒํผ ๋๋ ์ ๋ ๊ฒฐ๊ณผ ํ๋ฉด ๋ณด์ฌ์ฃผ๊ธฐ

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

- ๊ฒฐ๊ณผ ํ๋ฉด ๊พธ๋ฉฐ์ฃผ๊ธฐ
  - pixabay : ๋ฌด๋ฃ ์ด๋ฏธ์ง

<br>

### 8. ๊ฐ๊ฐ ๋ค๋ฅธ ๊ฒฐ๊ณผ ํ๋ฉด์ด ๋์ฌ ์ ์๋ ๋ก์ง ๊ตฌํ

- input์ ์ ์๋ค์ ํ์ฉํด์ ๊ฒฐ๊ณผ ๊ณ์ฐ
- ๋ง์ง๋ง ๋ฌธ์ ๋ฅผ ๋ค ํ์์ ๋ ๊ฒฐ๊ณผ๊ฐ ๊ณ์ฐ ํด์ผ ํ๊ธฐ ๋๋ฌธ์ next() ํจ์ ์์ ๊ตฌํ
- ๊ฐ์ด 2 ์ด์์ด๋ฉด ์์ ๊ฒ (E, S, T, J) / ๊ฐ์ด 2 ๋ฏธ๋ง์ด๋ฉด ๋ค์ ๊ฒ (I, N, F, P) ์ ํ

```html
<script>
  $("#EI").val() < 2 ? (mbti += "I") : (mbti += "E");
  $("#SN").val() < 2 ? (mbti += "N") : (mbti += "S");
  $("#TF").val() < 2 ? (mbti += "F") : (mbti += "T");
  $("#JP").val() < 2 ? (mbti += "P") : (mbti += "J");
</script>
```

<br>

### 9. MBTI์ ๋ง๋ ๋๋ฌผ 
- JavaScript ๊ฐ์ฒด ์์ ์ ์ฅํด๋์๋ค๊ฐ ๋งคํ
```html
<script>
    const result = {
        "ISTJ" : {"animal": "ํ๋ง", "explain": "ํ๋ง ์ค๋ช", "img": "lion.jpg"},
        "ENTP" : {"animal": "ํ๋ง", "explain": "ํ๋ง ์ค๋ช", "img": "lion.jpg"},
        "INFJ" : {"animal": "ํ๋ง", "explain": "ํ๋ง ์ค๋ช", "img": "lion.jpg"}
        ...
        }
</script>
```
- ๋ง์ง๋ง ํ๋ฉด์์ ํด๋นํ๋ ๊ฐ ๋ถ๋ฌ์ค๊ธฐ
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

## ๋ฐฐํฌํ๊ธฐ
- netlify ์ฌ์ฉ
- netlify.com ์ ์ > ํ์๊ฐ์ > Sites > ์์ํ ํด๋ ๋์ด์ค๊ธฐ > ์๋ ๋ฐฐํฌ
- site ์ด๋ฆ ๋ฐ๊พธ๊ธฐ : site settings > change site name 

<br>
<br>
<br>

## SNS ๊ณต์  ๊ธฐ๋ฅ ๋ง๋ค๊ธฐ
- AddThis ์ฌ์ฉ
- addthis.com ์ ์ > ํ์๊ฐ์ > Share buttons > Select Tool Type์ผ๋ก ์ํ๋ ๋ฒํผ ์ ํ > continue > sns ํ์ ์ ํ > activate tool > script ๋ณต์ฌ > body ํ๊ทธ ์์ ๋ถ์ฌ๋ฃ๊ธฐ > inline์์ div ํ๊ทธ ๋ณต์ฌ ํ ์ํ๋ ์์น์ ๋ถ์ฌ๋ฃ๊ธฐ

<br>
<br>
<br>

## ๊ด๊ณ  ๋ถ์ฌ์ ์์ตํ

### 1. ์ ๋ ๋คํธ์ํฌ (Google Adsense, KaKao Adfit)
- KaKao Adfit ์ฌ์ฉ
- KaKao Adfit ์ ์ > ๋ก๊ทธ์ธ > ๊ด๊ณ  ๊ด๋ฆฌ > ์ ๋งค์ฒด > ๋งค์ฒด : ํ๋ก์ ํธ ์ด๋ฆ, ๋งค์ฒด ๊ณ ์ ๊ฐ : ํ๋ก์ ํธ url > ๊ด๊ณ  ๋จ์ ๋ฑ๋ก > ๊ด๊ณ  ๋จ์ ๋ช: (์) ํ๋จ ๋ฐฐ๋1 > ์คํฌ๋ฆฝํธ sdk ๋ฐ๊ธ > ์ฝ๋ ๋ณต์ฌ > ๊ด๊ณ  ๋ฃ๊ณ  ์ถ์ ๊ณณ์ ๋ถ์ฌ๋ฃ๊ธฐ

<br>

### 2. ์ง์  ๊ด๊ณ  ๊ณ์ฝ
- ์์๋ฃ ์์
- ๊ด๊ณ ์ฃผ์๊ฒ ์ด๋ฏธ์ง์ url ์ ๊ณต ๋ฐ์์ผ ํจ
```
<!-- ์ -->
https://www.codelion.net/catalog?utm_source=animal_test&utm_medium=web_lecture&utm_campaign=jocoding
```
- utm ์ฝ๋ : ์ฌ์ดํธ์ ๋๋ฌํ๊ฒ ๋๋ฉด ์ด๋์๋ถํฐ ์๋์ง ์ถ์ 
- utm_campaign : ์์ ์ id
- ์ํ๋ ๊ณณ์ ๊ด๊ณ  ๋ถ์ฐฉ
```html
<a href="https://www.codelion.net/catalog?utm_source=animal_test&utm_medium=web_lecture&utm_campaign=jocoding">
    <img src="ad.jpg" alt="ad">
</a>
```

<br>
<br>
<br>

## ์ฌ์ดํธ ๊ฒ์๋๋๋ก ๋ง๋ค๊ธฐ

### 1. ๋ค์ด๋ฒ ๊ฒ์์ ๋์ค๋ ค๋ฉด?
- ๋ค์ด๋ฒ ์น๋ง์คํฐ ๋๊ตฌ์ ๋ด ์ฌ์ดํธ ๋ฑ๋ก
- ๊ฒ์ ๊ด๋ จ ๋ฌธ์ ์ ์ถ

<br>

### 2. ๊ฒ์ ์์ง์ ์๋ฆฌ
- ํฌ๋กค๋ฌ๊ฐ ์ธํฐ๋ท์ ๋์๋ค๋๋ฉด์ ์ฌ์ดํธ์ ๋ํ ์ ๋ณด๋ฅผ ์์งํ๊ณ  ๋ค์ด๋ฒ์ ์ ์ฅ, ๋ค์ด๋ฒ์์ ๋ง์ ์ฌ์ดํธ๋ค์ด ๊ฒ์๋๋๋ก ํด์ค
- robots.txt ๋ผ๋ ๋ฌธ์์ ์ ๋ณด ์์ฑ ํ ํฌ๋กค๋ง์ด ๊ฐ๋ฅํ์ง ๊ฒ์ฌ
- sitemap.xml : ํฌ๋กค๋ฌ๊ฐ ํฌ๋กค๋ง์ ์ ํ  ์ ์๋๋ก ํด์ค

<br>

### 3. ๋ค์ด๋ฒ ์น๋ง์คํฐ ๋๊ตฌ์ ๋ด ์ฌ์ดํธ ๋ฑ๋ก
- searchadvisor.naver.com ์ ์ > ์น๋ง์คํฐ ๋๊ตฌ > ๋ก๊ทธ์ธ > ์ฌ์ดํธ ๋ฑ๋ก์ url ๋ฑ๋ก > ๋ค์ > ์ฌ์ดํธ ์์  ํ์ธ (์๋ฌด๊ฑฐ๋ ์ฌ์ฉ) 
- ๋ฑ๋กํ ์ฌ์ดํธ ํด๋ฆญ > ๊ฒ์ฆ > robots.txt > robots.txt ๊ฐ๋จ ์์ฑ > ๋ชจ๋  ๊ฒ์ ๋ก๋ด, ์์ง ํ์ฉ > ๋ค์ด๋ก๋ > ๋ค์ด๋ฐ์ ํ์ผ์ ์์ํ๋ ํด๋์ ๋ฃ์ด์ค 
- ๊ตฌ๊ธ์ sitemap generator ๊ฒ์ > url ์๋ ฅ > start > ๋ค์ด๋ก๋ > ๋ค์ด๋ฐ์ ํ์ผ์ ์์ํ๋ ํด๋์ ๋ฃ์ด์ค
- robots.txt, sitemap.xml์ ์ถ๊ฐํ ํด๋๋ฅผ netlify ์ฌ์ดํธ์์ ์๋ฐ์ดํธ ํด์ค
- ์น๋ง์คํฐ ๋๊ตฌ > ์์ง์์ฒญ / ์์ฒญ > ์ฌ์ดํธ๋งต ์ ์ถ > url์ sitemap.xml ์๋ ฅ > ํ์ธ

<br>
<br>
<br>

## ๊ฒ์์์ง ์ต์ ํ (SEO)

### 1. SEO๋?
- Search Engine Optimization : ๊ฒ์์ด ์ ๋  ์ ์๋๋ก ์ต์ ํ
- SEO๊ฐ ์ ๋ ์๋ก ์๋จ์ ๋ฐฐ์น

<br>

### 2. ๊ฒ์์์ง ์ต์ ํํ๊ธฐ
- ๋ด๋ถ ์์ ์ต์ ํ (HTML, ์ปจํ์ธ , ๋ฉํํ๊ทธ ๋ฑ)
- ์ธ๋ถ ์์ ์ต์ ํ (๋ฐฑ๋งํฌ ๊ฐ์ ๋ฑ)

<br>

### 3. ์ต์ ํ ํ๋ ๋ฐฉ๋ฒ
- ๋ค์ด๋ฒ search advisor > ์ง๋จํ๊ธฐ > ์ฌ์ดํธ ๊ฐ๋จ ์ฒดํฌ > url ์๋ ฅ > ์ต์ ํ ์ํ๋ฅผ ๋ณด๊ณ  ๊ณ ์น๊ธฐ

