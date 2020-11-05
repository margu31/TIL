## user-select

텍스트를 선택(드래그)할 수 있는지 여부를 지정할 수 있다.

[속성값]

- none : 텍스트 선택 불가
- auto : 기본값으로 브라우저 허용시 텍스트 선택 가능
- text : 텍스트 선택 가능
- all : 클릭만으로도 선택 가능

버튼안에 있는 텍스트에 none 값을 적용하지 않았을 때, 모바일에서 해당 버튼을 조금 길게 누르면 버튼이 눌리지 않고 텍스트가 드래그되어 버리는 현상이 발생한다. 이를 방지하기 위해 none값을 부여해준다.

```html
<div class="button-container">
   <button type="submit" class="button-login" disabled="disabled">로그인</button>
   <a href="./signup.html" class="link-signup">회원가입</a>
</div>
```

```css
.button-container {
  margin-top: 155px;
  user-select: none;
}
```

## Checkbox Styling

input 태그의 checkbox 타입은 css로 스타일을 입히는 것이 제한적이다. 그래서 보통 input 옆에 span을 위치시키고 span 태그에다가 스타일을 입혀준다.

```html
<div class="save-email">
   <input type="checkbox" id="userEmailSave" />
   <span class="checkbox"></span>
   <label for="userEmailSave">이메일 저장</label>
</div>
<!-- input id값과 label for 속성을 이용해 두개를 연결해줬다.
이렇게 하면 웹 접근성이 좋을 뿐만 아니라, label요소 안의 text를 눌러도
연결된 checkbox 또는 radio가 체크되기 때문에 사용자 경험에도 좋다. -->

```

span에 스타일을 입히고 투명한 체크박스 밑으로(z-index) 보내주면 체크박스에 스타일을 준 듯한 효과를 볼 수 있다.

```css
.save-email {
  position: relative;
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
}
.save-email input {
  position: relative;
  z-index: 10;
  width: 16px;
  height: 16px;
  opacity: 0;
}
.save-email .checkbox {
  position: absolute;
  width: 16px;
  height: 16px;
  top: 50%;
  left: 0;
  transform: translateY(-50%); /* 가운데로 배치하기 위함 */
  background: url(./icon-un-checked.svg) no-repeat 0 0;
}
```

## `:checked` 가상 클래스

체크박스(`<input type="checkbox">`) 또는 라디오 버튼(`<input type="radio">`)이 선택 상태일 때 적용되는 선택자이다.

```css
.save-email input:checked + .checkbox {
  background-image: url(./icon-checked.svg);
}
/* save-email 클래스의 자식요소 input의 체크박스가 선택 상태가 됐을 때,
checkbox 클래스를 가진 형제요소를 찾아라! */
```

---

[오늘의 Chat] 

- 동공지진의 연속이다. 손도 제대로 못 대고 있다가 설명을 들으면 또 오..! 한다. 
알고 있는 것도 제대로 적용하지 못하고 설명 듣거나 완성된 코드를 봐야 아~ 이렇게 하면 되는구나~ 하고 있다. 
아는 걸 어떻게 끄집어내고 활용해야하는지..많이 해볼 수 밖에 없는 것 같다.
- 일본어로 된 사이트를 보다가 궁금한 것이 생겼다. margin이나 padding에 `block-start`, `block-end` , `inline-start` , `inline-end` 를 붙여서 쓴 코드를 봤다. 찾아보니 일본어 또는 몽골어와 같은 column 방향으로 흐르는 언어를 사용할 때 논리적인 방향에 맞춰 이와같은 속성을 사용한다고 한다. 물론, row방향으로 흐르는 언어들에도 사용 가능한 속성이다.
그런데 여기서 또 다시 궁금한 것이, 일반적인 언어의 흐름인 horizontal 방식으로 작성된 일본어 페이지에 왜 top, bottom, left, right를 쓰지 않고 block-start, inline-start와 같은 속성을 썼느냔 말이다. writing-mode가 vertical일 때에만 그렇게 쓰면 되지 않을까? 
궁금하다!
