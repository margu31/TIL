## 마진 병합 규칙 예외

`float: left / right` , `position: absolute` , `display: flex` , `display: grid` 는 마진 병합 일어나지 않는다. 

---

## float

float된 요소는 normal flow의 형제 요소에 영향을 줄 수 없다. 기본적으로 line-box를 기준으로 왼쪽, 오른쪽으로만 움직인다. 

---

## inline 요소의 vertical-align

inline 요소(ex, img, input, span)는 기본적으로 vertical-align 값이 baseline으로 문자의 하행선에 맞춰져 있다. 반면에 block 요소는 bottom에 맞춰져 있기 때문에 블록 요소 안에 이미지 요소(inline요소)를 넣을 경우 이미지 하단에 작은 갭이 생긴다.  이는 inline 요소의 vertical-align이 baseline을 default 값으로 갖기 때문이다. 영문자의 하행문자(decender) 표현을 위한 공간이다.

이 갭을 없애고 싶으면 inline 요소의 display 값을 block으로 설정하거나 vertical-align 값을 top으로 지정해주면 된다.  

[참고하기 좋은 블로그 글!](https://velog.io/@ursr0706/vertical-align)

---

## `<input>` 의 속성

- required : 불린(boolean)값으로 필수 입력 서식을 표현한다. 이 값을 넣어줬을 때 해당 입력창에 아무런 정보를 입력하지 않으면 서버로 전송되지 않는다.
- name : id 값과는 다르다! name 속성에 넣어주는 값은 서버로 전달되는 이름이다.

---

## `<form>`

- 항상 `fieldset`, `legend` 와 세트로 묶어서 사용하는 습관을 들이자.
- 암묵적으로 새로운 구역이 생겼으면 form 태그만 작성하지 말고 div든, section 이든 사용하여 명시적으로 구분을 해주자.
- fieldset 은 기본 스타일 자체에 테두리 선이 있다.
- form 태그와 fieldset 태그에는 보통 직접 스타일링을 입히지 않는다.

```html
<!-- 내가 작성해본 코드 -->

<form class="search-form" action="">
    <span class="icon-serch" aria-hidden="true"></span>
    <label for="searchForm">자료검색</label>
    <input type="text" id="searchForm" placeholder="검색어를 입력하세요.">
    <button type="submit">검색</button>
</form>
```

```html
<!-- 수업에서 사용한 코드 -->

<div class="group group2">
  <h2 class="a11y-hidden">검색</h2>
  <form method="POST" action="https://formspree.io/seulbinim@gmail.com" class="search-form">
     <fieldset>
        <legend>검색 폼</legend>
        <div class="seach-from-container">
           <label for="search"><span class="icon-search"></span>자료검색</label>
           <input type="search" id="search" name="search" required placeholder="검색어를 입력하세요.">
           <button class="btn-search" type="submit">검색</button>
        </div>
     </fieldset>
  </form>
</div>
```

---

## background

- `{ background: #ccc, linear-gradient(#ccc, #eee) }`
이 때, 앞의 값은 뒤에 그라데이션이 지원되지 않는 환경에서 활용할 색을 지정해준 것이다.  (콜백디자인)
- `{ background: url(./images/validation_icon.png) no-repeat 25px 50% / 20px 20px, linear-gradient(to bottom, #eee, #ccc); }`
앞 쪽에 위치한 숫자는 위치를 나타내고, '/' 뒤의 숫자는 이미지의 크기를 의미한다.

---

[오늘의 Chat]

1. 마크업도 설계하고, 그 다음 디자인도 설계해본 뒤에 코드로 옮기는 습관을 들여보자!
2. 설계 그림을 그릴 때도 인라인 요소는 옆으로 그리고, 블록 요소는 수직으로 쌓아서 그리자!
3. 마크업도 아직 익숙하지 않지만 CSS로 레이아웃 짜는게 너무 어렵게 느껴지고 어떻게 하는게 좋을지 잘 떠오르지 않는다. 많이 부족한 것 같다. 시각적으로만 생각하지 않고 좀 더 효율적인 방법을 찾는 연습을 해야겠다.
4. 나는 아주 조금씩이지만 매일 나아지고 있다..!!