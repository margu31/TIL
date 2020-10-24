## text-indent

text-indent 블록 요소에만 적용 가능한 CSS 속성으로, 들여쓰기와 내어쓰기에 사용한다.
양수 값은 들여쓰기, 음수 값은 내어쓰기가 된다.

---

## `<Form>` 태그

서버에 정보를 제출하기 위한 입력 양식의 범위를 지정하는 태그이다. 예를들어, 로그인 또는 회원가입 양식 등이 있다.

`<form>` 태그 내에 쓸 수 있는 태그 중 `fieldset` 과 `legend` 태그가 있는데 XHTML에서는 필수로 작성해줘야 하고, HTML 4.01에서는 쓰지 않아도 괜찮다. HTML5 같은 경우에는 두 문법체계를 다 허용하기 때문에 써도 OK, 안 써도 OK!

그렇지만, 좀 더 직관적으로 코드상에 명시하고, 기계한테 친절하게 알려주기 위해 쓰는 편이 더 좋지 않을까 ..

- `<fieldset>` : 관련있는, 즉 같은 목적의 양식들을 묶어 그룹화 해줄 때 사용
- `<legend>` : 해당 서식 그룹(`fieldset`)의 설명 또는 제목을 정의할 때 사용
- 두 태그를 사용하면 접근성 측면에서도 좋다! legend 태그에 넣은 내용을 스크린리더가 읽어주기 때문이다. 디자인상 해당 내용이 화면에 노출되지 않기를 원하면 `숨김 콘텐츠`로 만들어버리면 된다!!

```html
<form method="POST" action="#서버주소" class="login-form">
  <fieldset>
    <legend>회원 로그인 폼</legend>
    <div class="user-email">
      <label for="userEmail">아이디</label>
      <input type="email" id="userEmail" name="userEmail" placeholder="이메일주소" required>
    </div>
    <div class="user-pw">
      <label for="userPw">비밀번호</label>
      <input type="password" id="userPw" name="userPw" placeholder="8자리이상" required>
    </div>
    <button class="btn-login" type="submit">로그인</button>
  </fieldset>
</form>
```

- 위의 코드에서 `label` 태그로 각각 아이디와 비밀번호 입력란(input)을 연결해줬는데, 이는 스크린리더에게도 해당 `input` 태그가 어떤 입력양식인지 명시적으로 알려주게 된다.  
'placeholder' 에 넣은 양식의 경우 입력창에 대한 hint만 제공할 뿐 정확히 어떤 입력창인지 의미를 알기 어렵다. (물론, 일반 사용자는 바로 의미를 알 수 있겠지만 스크린리더 등 보조기구로 접근하는 사용자에게는 그 의미를 알기 쉽지 않다.)
- `label` 태그를 사용하지 않고, `input` 태그만을 사용하고 싶다면 `title` 속성을 꼭 넣어주자!
- 위의 코드 입력 방식은 명시적 표기법이고, 아래처럼 `label` 태그를 `for` 속성없이 암묵적으로 `input` 태그와 연결시켜 주는 방법은 최근 스크린리더기 사용에 문제가 종종 나타나고 있다고 하니 명시적 방법을 사용하도록 하자.

```html
<label>
   비밀번호
   <input type="password" id="userPw" name="userPw" placeholder="8자리이상" required>
</label>
```

---

## `vertical-align` / `text-align`

- vertical-align : 인라인 개체한테 주는 속성으로 세로선을 기준으로 정렬 (수직 정렬) - img (또는 icon)와 text의 수직 라인을 수평하게 맞추기 위해 많이 쓰이는 듯 하다. 
수업 시간에는 입력창(input)과 text의 높이를 맞추기 위해 사용했다.
- text-align : 블록 요소의 가로 정렬에 쓰임 (문단 정렬)
- [viertical-align 도움되는 페이지](http://blog.hivelab.co.kr/%EA%B3%B5%EC%9C%A0-vertical-align-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0-1%EB%B6%80/)

---

## `<button>`

`button` 태그 사용 시에 padding 값을 재정의 하는게 좋다. 왜냐하면 브라우저마다 기본값이 다르기 때문에 재정의 하지 않으면 원하는 스타일링이 나오지 않을 수 있고, 브라우저마다 다르게 랜더링될 수 있다.

- `a` 태그 안에 `button` 태그는 올 수 없다. 즉, `<button>`은 부모 요소로 `<a>`를 둘 수 없다.
- `<button>`의 type 속성에는 button, reset, submit이 있다.
- 링크 기능이 삽입된 버튼을 만들고 싶은 경우, `button` 태그를 쓰지 않는다!! 기능적 측면으로 봤을 때 `a` 태그를 쓰는게 맞고, CSS로 스타일링을 버튼 모양으로 만들어 주면 된다.  → 버튼 모양이라고 다 `<button>`으로 마크업 하려고 하지 말자.

---

## white-space

공백 문자 처리 방법을 정하는 속성으로 줄바꿈 처리할 때 자주 사용한다. 

- normal - 기본값
연속된 공백은 1개의 공백으로 병합하여 출력하고 영역의 크기 안에서 자동 줄바꿈 된다.
- nowrap  
기본값인 normal과 동일하게 2개 이상의 공백은 병합하여 1개의 공백으로 처리하지만, 자동줄바꿈 되지 않는다.
- pre  
연속된 공백을 그대로 출력하고, 긴 내용의 글이라도  자동 줄바꿈 되지 않는다.
- pre-wrap  
연속 공백 그대로 유지, 자동 줄바꿈 된다.
- pre-line
2개 이상의 공백은 병합하여 1개의 공백으로 표시하고 자동 줄바꿈 된다

---

## letter-spacing

글자 사이의 간격을 조정하는 속성이다. 음수값도 사용 가능하지만 글자가 겹칠 수 있다. 
글자 간격이 너무 크거나 작으면 가독성이 좋지 않기 때문에 사용에 주의해야 한다.

단어 사이의 간격은 `word-spacing` 이란 속성을 사용한다.

---

## `<article>` / `<section>`

- article : 독립된 콘텐츠로 RSS (Rich Site Summary) 피드로 배포할 가치를 가지는 하나의 포스트, 하나의 주제로 완결되는 내용.
 예시> 블로그 글, 뉴스 기사, 포럼 글, 매거진 등
- section : 관계가 있는 문서를 세분화해 다른 주제로 구분짓기 위해 사용. 하나의 대주제 안에 여러 소주제가 있는 경우를 생각하면 된다.

---

## `<dl>` , `<dt>` , `<dd>`

Description-List, Description-Term, Description-Description의 약자이며, `<dl>` 은 자식요소로 `<dt>`와 `<dd>`만 취한다.

key=value 일 때 쓰기 적합하다.  즉, `dt` 와 `dd` 가 1:1로 쌍을 이룰 때 사용하기를 권장한다고 한다. 아직 사용법이 많이 와닿지는 않아 좀 더 고민해봐야겠다.

HTML 5.2 에서 `dl` 태그 내에 `div` 태그를 사용할 수 있게 되었다고 한다. 그러나 `dl` 태그 안의 `div` 는 child로 `<dt>`와 `<dd>`만 가져올 수 있다.

```html
<section class="term">
  <h2 class="term-heading">웹 관련 용어</h2>
  <dl class="term-list">             
     <div class="odd">
        <dt class="term-list-subject">웹 표준 이란?</dt>
        <dd class="term-list-thumbnail">
          <img src="images/web_standards.gif" alt="W3C 로고">
        </dd>
        <dd class="term-list-brief">
          W3C 단체에서 규정한 웹 기술 사양에 대한 규칙을 말하며.. 
        </dd> 
     </div>
  </dl>
</section>
```

---

## etc..

- `::before` 로 선언한 icon 등은 Javascript 로 제어가 불가능하다. 제어 목적이 없는 단순 장식 등의 img 또는 icon 등은 ::before 또는 ::after 로 삽입 가능하다.
- 기술부채 (Technical Debt, Code Debt) - 더 나은 방법을 채택하는 대신 현재 편하고 쉬운 솔루션을 선택함으로써 일단 당장 앞의 비즈니스 이슈를 해결하며 생기는 빚이라고 한다.
- 파싱(Parsing) ?
구문 분석, 문장이 이루고 있는 구성 성분을 분해하고 관계를 분석하여 구조를 결정하는 것. 즉, 데이터를 분해 분석하여 원하는 형태로 조립하고 다시 빼내는 프로그램을 말한다. 웹 상에서 주어진 정보를 원하는 형태로 가공하여 서버에서 불러들이는 것이다.  
출처 - 해시넷

---

[오늘의 Chat] 

파싱도 그렇고 종종 언급되는 처음 듣는 전문 용어들이 나오면 무슨 뜻인지 알아 듣기 어렵다. 인터넷에 찾아보고 읽어봐도 와닿지 않는 말들이 많다. 점점 익숙해지고 아! 그 말이 이런 뜻이구나, 이럴 때 쓰이는구나! 하고 알게 되는 날이 왔으면 좋겠다!