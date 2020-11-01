## CSS로 넘버링 하기

HTML에 마크업 하지 않고 CSS로 목록의 넘버링을 할 수 있다. 

`counter-reset` - 카운터를 새로 지정하거나, 초기화 

`counter-increment` - 카운터 증가 값을 지정

`counter()` - 카운터 함수 선언

▶ 사용방법

```css
{counter-reset: 카운터명 시작숫자;}
{counter-increment: 카운터명 증감숫자;}
{content: counter(카운터명 스타일);}
```

counter-reset에 시작 숫자를 지정하지 않으면 기본값은 0이다. 음수값도 사용 가능

counter-increment에 증감 숫자를 적지 않으면 기본값으로 1씩 증가한다. 음수값을 설정하면 감소하게 된다.

counter() 에서 스타일의 기본값은 십진수이고, 로마자로도 지정할 수 있다.

```html
<ol class="favorite-list">
   <li><a href="#">W3C</a></li>
   <li><a href="#">Git&amp;Github</a></li>
   <li><a href="#">MDN</a></li>
   <li><a href="#">Fastcampus</a></li>
</ol>
```

```css
.favorite-list {
  padding-left: 0; /* 리스트가 가지고 있는 기본 왼쪽 패딩값 초기화 */
  list-style: none; /* 기본 스타일 삭제 */
}
.favorite-list li {
  counter-increment: number;
}
.favorite-list li::before {
  content: counter(number);
```

## IR (Image Replacement) 기법

스크린리더 사용자를 위한 기법으로, 이미지에 추가 설명을 제공할 때 주로 사용한다. 

보통 대체 텍스트를 제공한다고 하면 alt 속성을 사용하지만, 좀 더 추가적인 설명이 필요하거나 내용이 긴 대체 텍스트를 제공해야하는 경우 IR 기법을 많이 사용한다. 특히, img 태그를 사용하지 않은 의미있는 배경 이미지에 자주 사용되는 방법이다. 

이때, 배경은 크기를 가져야한다. (width, height) 그렇기 때문에 인라인 요소는 display: inline-block 으로 처리해줘야 한다. 

text를 숨길 때에는 padding 트릭을 사용할 수 있다. padding-top을 배경 이미지 높이만큼 지정하고 height: 0; 그리고 overflow: hidden 으로 설정하면 배경 이미지만 보이고 텍스트는 보이지 않는다. 

## Image Sprite

웹에서 많이 사용하는 이미지 방식으로, 사이트에서 사용되는 여러 개의 이미지를 하나의 파일로 만들고 필요한 이미지 영역만 위치를 지정하여 보여준다.

필요한 크고 작은 이미지를 한 데 묶어놨기 때문에 매번 이미지를 호출하지 않아도 되어 불러오는 속도가 빠르다. 

배경 position은 px 단위 외에 %로 지정할 수도 있다. 

```css
.up, .down, .stop {
  width: 9px;
  height: 0;
  overflow: hidden;
  padding-top: 11px;
  background: transparent url(./images/rank.png) no-repeat;
  position: absolute;
  right: 0;
  top: 50%;
  margin-top: -5px;
}
.up {
  background-position: 0 0;
}
.down {
  background-position: 0 100%;
}
.stop {
  background-position: 0 50%;
}
```

## 가상 요소를 이용한 이미지 삽입

HTML 문서에서 마크업 하지 않고, 가상 요소로 이미지를 삽입하는 것이 가능하다. 

`{content: url();}` 로 이미지를 넣어줄 수 있다. 다만, 이렇게 이미지를 추가하는 경우 사이즈 조절은 불가하다. 

이미지 크기를 조절해야 한다면, `{content: "";}` 콘텐트에는 내용을 비우고, display값은 block으로 변경, background에 이미지를 깔아주는 방법으로 가능하다. 

```css
.slogan-heading::after {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: url(./images/coffee.png) no-repeat 0 0;
}
```

## 인용구 - `<q>` & `<blockquote>`

`q` : 문단 내에 들어있는 짧은 인용구, inline 요소

`blockquote` : 새로운 문단으로 만들어진 긴 인용구, block 요소

q태그에는 따옴표 ("")가 앞뒤로 자동으로 삽입되는데, 이는 `q::after { content: ""; }` 이런식으로 없애줄 수도 있고, `q { quotes: "[" "]"; }` 로 따옴표를 다른 기호로 바꿔줄 수도 있다.

## text-transform

대문자 또는 소문자로 바꿔주는 속성이다.

- none : 기본값으로 입력된대로 출력
- capitalize : 각 단어의 첫번째 글자만 대문자로 변경
- uppercase : 모든 글자를 대문자로 변경
- lowercase : 모든 글자를 소문자로 변경

## Skip-Navigation

tab키를 이용해 주소창에서 바로 핵심 영역인 본문으로 넘어갈 수 있게 `skip-navigation` 을 만들어줘야한다. body태그 안 바로 처음에 마크업!

이 때, main 영역에 id 값을 부여하고 a태그를 이용해 해당 구역으로 넘어갈 수 있게 처리해준다.

CSS로 화면에서 숨김 처리를 하고 포커스를 받으면 나타나게 해준다.

```html
<div class="skip-nav"><a href="#content">본문 바로가기</a></div>
.
.
<main class="main" id="content">
.
.
</main>
```

```css
.skip-nav a {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 0;
  overflow: hidden;
  background-color: #000;
  color: #fff;
  padding: 0;
  text-align: center;
  z-index: 10;
}
.skip-nav a:focus {
  height: auto;
  padding: 10px 0;
}
```

## etc,

1. 가상 요소는 JavaScript로 접근할 수 없다. 돔객체가 잡히지 않기 때문
2. 마우스로 동작 가능한 환경에 익숙하지만 항상 키보드로도 접근 가능한 환경을 만드려고 노력해야한다.
3. `<small>` 덧붙이는 글에 사용하는 작은 글씨 태그로 주로 저작권, 법률 표기 같은 내용에 쓰인다.
4. ISBN (International Standard Book Number) 국제 표준 도서 번호
5. 출처, 저작권에 대해 잘 명시하자! 

```html
/* 슬로건 영역 */
<footer class="a11y-hidden">
      출처 : W3C, http://w3.org/WAI/
</footer>
```