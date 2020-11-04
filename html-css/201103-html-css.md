## `<svg>`

Scalable Vector Graphics의 약자이며, 벡터 이미지를 만드는 태그이다. 

[참고하기](https://nykim.work/35)

## 이미지와 `<a>` 의 만남

이미지에 `visibility: hidden;` 을 주면, 시야에서 보이지는 않지만, 본래 자리의 영역을 그대로 차지하고 있다. 

`{visibility: hidden;}` 된 이미지의 본래 자리에 a태그가 겹쳐있거나, 그림의 투명 처리된 일부 영역이 a 태그를 가리면 링크가 눌리지 않는다. 

그렇기 때문에, 링크 영역의 어디를 눌러도 a 태그가 실행되게 해주려면 이미지보다 `<a>` 를 위에 올려줘야 한다.

만약 이미지가 position: relative 값을 지녀 위에 떠 있으면, a태그도 포지션값을 줘서 띄워줘야하는데 이때 마크업상 a가 먼저 선언됐다면 여전히 a태그는 겹쳐진 부분에서 마우스가 손모양으로 활성화 되지 않는다. 

그럴때에는 z-index 속성을 이용해 a태그를 이미지보다 위로 올려주면 된다!

## margin & padding - percentage (%)

margin과 padding에는 %로도 값을 부여할 수 있는데, 이때 여백의 크기는 부모 컨테이닝, 즉 부모의 컨테이너 박스 너비(width)를 기준으로 한다.

## flex-shrink

flexible 이미지에 넓이를 고정시켜 지정해줘도 디바이스 뷰포트가 줄어들면 비율에 따라 너비도 줄어들 수 있다. 때문에, 디바이스가 작아지더라도 너비를 고정시키고 싶은 요소가 있다면 flex-shrink 값으로 0을 부여하면 된다. 그럼, 해당 요소는 뷰포트가 작아져도 부여받은 너비를 유지한다. 

```css
/* headline은 디바이스 크기가 작아지더라고 고정된 너비 125px을 유지하고,
   늘어난 영역은 flex-grow: 1;을 가진 article이 채워지게 된다. */
.ediya-notice-headline {
  width: 125px;
  flex-shrink: 0;
  background: var(--theme-primary);
  color: var(--theme-bright);
  margin: 0;
}
.ediya-notice__article {
  flex-grow: 1;
  background: var(--theme-bright);
}
```

## etc,

- 인라인 요소를 줄바꿈하기 위한 방법으로는 white-space를 이용하거나, display: block으로 변경 또는 flex-direction을 column으로 주는 방법이 있다.   
아래 예제에서는 em태그에 display: block;을 줘서 줄바꿈 처리했다.

```html
<p class="ediya-recommend-text" lang="en">ALWAYS BESIDE YOU  <em class="theme-blue">EDIYA COFFEE</em></p>
```

- position: fixed / sticky  
fixed는 고정된 위치에 머무르고 있어 스크롤을 쭉 내리면 위로 올라가서 보이지 않는다.  
sticky는 유효한? 딱 보이는 디바이스 뷰포트 내에 지정한 위치에 계속 붙어 있어서 스크롤을 내려도 그 위치에 고정되어 있다.
- `:root` 전역 css 변수 선언에 사용한다. 브랜드 컬러 등 전반적으로 사용되는 스타일링을 미리 지정해두고 가져와 쓰게 된다.

```css
:root {
  --theme-bright: #fff;
  --theme-default: #14182c;
  --theme-primary: #24388d;
  --theme-secondary: #bae5fb;
}
```

- iframe과 video
크롬 브라우저?에서는 접근성 문제로 autoplay 사용 불가(스크린리더와 오디오 겹침) - 꼭 autoplay를 사용해야한다면 음소거 모드로 설정해두어야 한다.  
자막(track 태그)가 있어야 한다!  
iframe - 유튜브 영상 가져올 때 많이 쓰임

---

[오늘의 Chat] 

고정형도 어렵지만 반응형도 정말 어렵다. 좀 더 생각해야할게 많은 것 같다. 코드도 디바이스 크기마다 나눠서 선언해줘야하고.. 뭔가 정신없다.   

한 페이지 만드는데에도 이렇게나 많은 코드가 존재하는데 현재 내가 아무렇지 않게 사용하는 사이트들은 대체 얼마나 많은 코드들이 복잡하게 얽혀있는걸까..   

개발자들의 많은 수고로 정말 편한 세상을 살고 있었다!