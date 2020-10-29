![예제 이미지](https://github.com/margu31/TIL/blob/main/html-css/img_1029.JPG)
## 예제 마크업 연습

첨부한 이미지의 마크업을 혼자 해봤을 때 이벤트 목록이 여러개가 있고, 그 중 하나만 화면상에 보이는 상태이며 버튼으로 다음 리스트 또는 이전 리스트 내용을 확인할 수 있는거라고 생각해 ul태그에 li태그를 만들고 또 그안에 img와 p태그를 넣는 방향으로 생각했다. 

그리고 그렇게 됐을 때 css로 어떻게 구현해야하지? 고민을 해봤는데 이런 움직임은 비동기 통신으로 내용 일부만을 갱신하는 것으로 css영역이 아닌 javascript로 해야한다는 것을 알았다!

또한, JavaScript로 제어를 해야하는 경우 컨트롤하기 수월하게끔 div로 묶어주고 id를 선언하는 방향이 좋다고 한다!

⇒ 수업에서 채택한 마크업은 이벤트 내용 전체를 div로 묶어주고 p 태그에 이미지 삽입, 또 하나의 p태그에 내용을 작성했다.

```html
<div id="eventDetail">
   <p class="event-thumbnail"><img src="./images/free_gift.gif" alt="이벤트 경품 : 웹표준 핵심 가이드북2 도서 증정"></p>
   <p class="event-brief"><em>웹표준 핵심 가이드북 2 출시! </em>선착순 500명 한정으로 증정.</p>
</div>
```

위 예제에서 놓치기 쉬운 POINT !

바로, 주황색 글씨 부분들이다. 따로 색을 넣어줘야하기 때문에 span, em, strong 같은 태그들로 묶어줘야 한다!

또 한가지 알아둘 것은, 신규 이벤트 부분의 내용을 시간에 따라 자동 갱신하도록 만들고 싶으면, 접근성을 고려해 정지 버튼과 재생 버튼도 만들어야한다.

## 접근성을 고려한 `<button>`

```html
<div class="btn-event">
   <button type="button" class="btn-prev">이전 이벤트 보기</button>
   <button type="button" class="btn-next">다음 이벤트 보기</button>
</div>
```

웹 접근성을 생각해 `<` 와 `>` 버튼에 설명을 추가하였을 때, 디자인 상으로는 해당 텍스트가 노출이 되면 안된다. 이 때, css로 텍스트 숨김 처리하기가 조금 까다롭다.

overflow: hidden 처리도 하고 text-indent로 글자도 버튼 안에서 밖으로 밀어버려야하고.. 

`aria-label` 을 이용하면 텍스트에 대한 고민이 간단히 해결된다! 

aria 속성을 잘 알아두고 활용하자.

```html
<div class="btn-event">
   <button type="button" class="btn-prev" aria-label="이전 이벤트 보기"></button>
   <button type="button" class="btn-next" aria-label="다음 이벤트 보기"></button>
</div>
```

## 애니메이션 효과 (Transition)

`@keyframes` 로 animation을 선언하지 않아도 애니메이션 효과를 낼 수 있는 속성이 바로 transition이다! 

당연하게 애니메이션 효과를 생각하면 animation 속성만 떠올렸는데 transition이 더 간단히 해결될 때가 있다는 걸 꼭 기억해야겠다. 

`transition` 은 시작하는 요소에 넣어줘야한다. `:hover` 에 넣어줘도 똑같이 작동하지만, 마우스가 해당 영역을 벗어났을 때 부드럽게 연결되어서 애니메이션이 원래 자리로 돌아오지 않고 한번에 뚝 끊겨서 돌아온다. 시작하는 요소에 넣어주면 마우스가 벗어나도 연결성있게 제자리로 스르륵 돌아온다.  

## 리플로우 (Reflow)

문서 내 요소의 위치와 도형을 다시 계산하기 위한 웹 브라우저 프로세스의 이름. 문서의 일부 또는 전체를 다시 렌더링하는 데 사용된다.

리플로우는 브라우저에서 사용자를 차단하는 작업이므로 리플로우를 최소화 해야한다고 한다.

## IR (Image Replacement) 기법

의미있는 이미지를 배경으로 처리하고, 그에 상응하는 내용을 텍스트로 기입하는 방법 

접근성을 떨어뜨리지 않으면서 검색엔진으로부터 높은 가중치를 받을 수 있다고 한다.

## IS (Image Sprite) 기법

조각난 이미지 파일들을 하나의 파일로 합친 후 배경으로 처리함으로써 웹 문서 전송 속도를 높이는 기법. 접근성 확보 때문에 IR 기법이 함께 사용된다고 한다. 

---

[오늘의 Chat] 

- 여전히 어려운 전문 용어들.. 오늘도 리플로우, IR, IS 기법 등은 그런게 있구나~ 하고 일단 넘어가야겠다.
- 익숙해질 때까지 반응형보다 고정형에 더 집중해서 학습하자!
- 동기 친구들과 한번 날 잡아서 함께 클론코딩을 하기로 했다! 항상 도움만 받고 있는데 분발해서 열심히 해야겠다.
- 강사님 말씀 들으면서 또 한번 접근성을 고려하는게 쉽지 않구나 느꼈다. 사용자로서 내가 경험한 것만 생각하다보니 아무래도 생각지도 못하는 부분에서 많이 놓치게 되는 것 같다. 아직 뭘 잘 모르기도 하고.. 직접 불편하신 분들의 얘기를 듣고 그분들에게 불편한 점을 개선해나가려고 하시는 모습이 정말 멋있으시다.