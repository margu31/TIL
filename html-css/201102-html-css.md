# '반응형 웹(Responsive Web)'

## One Source Multy Use

하나의 소스로 다양한 디바이스를 지원.

## DeskTop First vs Mobile First

B2B 서비스는 주로 Desktop 위주의 디자인을 우선하고, B2C 서비스의 경우에는 모바일 서비스에 집중하는 경향이 있다고 한다. 

스마트폰의 보급으로 인해 데스크탑 보다는 모바일 웹이나 앱의 활용이 높아짐에 따라 새로 출시되는 서비스는 대부분 모바일 대응을 우선시하는 분위기인 것 같다. 

그 외에.. UI 배치 등 화면 구성이 모바일 먼저 하고 데스크탑을 진행하는게 더 수월하다는 것 같았는데.. 다시 좀 더 알아봐야겠다.

## `<picture>`

반응형 이미지(Resposive Images)를 구현하기 위해 사용되는 태그로, 0개 이상의 `source` 태그와 1개의 `img` 태그로 구성된다.

뷰포트(viewport)의 너비에 따라 이미지가 커지거나 작아지는게 아니고 여러 크기의 이미지를 제시해놓고 브라우저가 그 중 가장 최적의 이미지를 찾아 사용할 수 있도록 하는 태그이다.

```html
<picture>
   <source media="(min-width: 1280px)" srcset="./margu_large.jpg">
   <source media="(min-width: 800px)" srcset="./margu_small.jpg">
   <img src="./margu_medium.jpg" alt="Margu-logo">
</picture>
```

`source` 요소에 제시된 조건을 만족하지 않는 경우에는 `<img>` 에 선언된 이미지를 사용하게 된다. 

picture 태그는 IE11에서 지원되지 않으며, img 태그에도 srcset 속성을 쓸 수 있는데 이 또한 IE 에서는 지원되지 않는다.

## `@media` 미디어쿼리

단말기 유형, 디바이스 뷰포트 또는 해상도 등 특정 조건에 따라 스타일을 적용할 때 사용한다.

- 미디어 유형  
all - 모든 장치  
print - 인쇄 결과물 및 출력 미리보기  
screen - 화면  
speech - 음성 장치 대상  

```css
@media all and (max-width:767px){
   /* 가로너비 767px 이하의 모든 미디어 장치에서의 스타일 적용 */
}
@media all and (min-width: 768px){
   /* 가로너비 768px 이상의 모든 미디어 장치에서의 스타일 적용*/
}
```

## Navigation 영역

링크 걸린 `<a>` 태그들의 묶음이 들어있는 navigation 영역에서 요소들 사이에 구분선이 따로 없다면 요소 사이의 거리는 padding이 아니라 margin으로 처리하는게 좋다. 

padding으로 처리하면 클릭할 수 있는 영역이 넓어져서 양쪽의 요소들의 영역 구분이 어렵다. 

## `margin: auto;`

text를 가운데 정렬하기 위해 사용되는 margin: auto;는 블럭 요소에만 적용된다. 
block element는 한줄의 모든 영역을 차지하고 있기 때문에 남는 공간을 쪼개 자신의 margin으로 만들 수 있다. 

반면, 블록 요소의 특징도 가지고 있는 inline-block element는 margin: auto; 적용이 불가능하다. 이는 block요소처럼 크기와 마진, 패딩을 가질 수 있지만, 기본적으로 inline 특성을 지녀 자신의 텍스트만큼 공간을 차지하고 수평으로 쌓이며 흐른다. 따라서 온전히 자신의 영역(line)을 가지고 있지 않기 때문에 자동으로 나눠가질 수 있는 margin이 없다. width를 지정해주더라도 다음 요소가 바로 옆에서 흐르기 때문에 margin: auto;는 사용할 수 없다.

## `backdrop-filter`

요소 뒤에 있는 영역에 그래픽 효과를 적용할 수 있다. 다만, 적용된 효과가 보이려면 요소 또는 요소의 배경이 불투명하면 안된다.

여기저기 사이트에서 많이 보이는 기법(?)이다!

```css
.app-navigation {
    backdrop-filter: blur(5px);
    background: hsla(225, 57%, 10%, 0.9);
    color: #fefefe;
}
```

[backdrop-filter](https://css-tricks.com/almanac/properties/b/backdrop-filter/)

## etc,

- 반응형 웹에서는 `Flexible Layout` , `Media Query` , `Responsive Image` 가 핵심이다!
- 이미지 최적화를 하는 편이 속도 등 성능적으로든 메모리 용량 측면으로든 좋다.
- 반응형 콘텐츠는 `max-width: 100%;` , `height: auto;` 로 설정한다.
- 반응형 사이트를 만들 때에는 주로 `vw` , `vh` 단위를 많이 사용한다.
- 아트 디렉션(Art Direction) ? 
반응형 웹에서 이미지의 의도가 제대로 전달될 수 있도록 디바이스 뷰포트에 따라 사진의 핵심 영역을 확대하거나 주변을 잘라버리거나 하는 것
- 다양한 이미지 파일 형식!
SVG, WebP, JPEG-XR, FlashPix
(gif, jpg, png 만 있는게 아니다!)
- polyfill ? 특정 기능이 지원되지 않는 브라우저에서 최신 기능을 사용할 수 있도록 하는데에 필요한 코드 - 최신 버전과 오래된 브라우저 사이의 간격을 메우는 충전솜!
- 확장 프로그램 lighthouse를 잘 이용하자! 접근성 외에도 `명도대비` 조건에도 부합하는지 알 수 있다. - 디자이너와 색상 등으로 얘기할 때에도 활용도 좋다!

---

[오늘의 Chat] 

순식간에 수업이 지나간다. 기초가 많이 부족하다는 것을 계속 느끼고 있다..  

### 한번 읽어보면 좋은 내용 첨부

[반응형 이미지](https://developer.mozilla.org/ko/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)

[What is Mobile First Design? Why It's Important & How To Make It?](https://medium.com/@Vincentxia77/what-is-mobile-first-design-why-its-important-how-to-make-it-7d3cf2e29d00)

[Mobile-First Web Design vs. Responsive Web Design](https://darwindigital.com/mobile-first-versus-responsive-web-design/)