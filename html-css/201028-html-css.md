## Layout Styling

CSS 레이아웃에는 여러가지 방법이 있다.

1. `display: inline-block`  
2. `position` 
3. `float` 
4. `display: flex` 
5. `display: grid` 

다양한 방법으로 만들어보고 어떤 속성을 사용할 때 가장 효율적인지 알아야한다.

## `<figure>` & `<figcaption>`

figure 태그는 삽화, 사진, 다이어그램 등 문서의 주요 흐름과는 독립적인 콘텐츠를 정의 할 때 사용한다. 해당 태그의 콘텐츠는 문서의 내용과 연관이 있지만, 제거하거나 위치 이동을 해도  문서의 흐름에 영향을 주어서는 안되는 독립적인 아이다!

figcaption은 figure와 함께 다니면서 설명을 보충해주는 태그이며, figure의 child 요소로 들어간다. 

## 구분선

구분선을 위한 마크업 없이 가상요소를 활용하는 방법이 있다. 
구분선이 필요한 곳의 위에 위치한 요소에는 `::after` , 아래에 위치한 요소에는 `::before` 를 이용해 상자를 만들어주고 배경 색상을 채워주면 된다.

```css
.news::before {
  content: "";
  position: absolute;
  top: 35px;
  left: 0;
  width: 100%;
  height: 1px;
  background:#ccc linear-gradient(to right, #ccc, #fff);
}
```

## '새소식' 구역 Mark-up

- 용어에 대한 설명은 아니기 때문에 dl, dt, dd 태그는 어울리지 않는 마크업이다.
- img, time, figure 등의 태그를 전부 `a` 로 묶는 것은 사용자 경험이 좋지 않지만, 가능한 방법이다.
- 제목인 h2 태그와 더보기의 a 태그가 연결됨을 명시하기 위해 h2 태그의 id를 aria-labelledby로 a 태그에 연결해준다.

```html
<section class="news">
   <h2 class="news-heading" id="newsHeading">새소식</h2>
   <article class="news-article">
      <a href="#" class="news-article-link">
         <h3 class="news-article-subject">
          W3C 사이트가 리뉴얼 되었습니다.
         </h3>
         <time class="news-article-date" datetime="2020-10-28T14:19:07">2020.10.28</time>
         <p class="news-article-brief">
          디자인 및 다양한 view 환경을 고려하여 구성되어 있으며,
          기존보다 최신 정보 및 개발자를 위한 기술 가이드도
          찾기 쉽도록 구성되어 있습니다.
         </p>
         <figure class="news-article-thumbnail">
            <img src="./images/news.gif" alt="" aria-labelledby="newsArticleThumbnail">
            <figcaption id="newsArticleThumbnail">W3C 리뉴얼</figcaption>
         </figure>
      </a>
   </article>
   <a href="#" class="icon-plus news-more" title="새소식" aria-labelledby="newsHeading">더보기</a>
</section>
```

## grid

FlexBox와 마찬가지로 Container와 Item이 있다. 
속성이 굉장히 많기 때문에 잘 알아두자! 

참고로 최신 레이아웃 기술이지만, 현업에서는 잘 사용할 기회가 없다고 한다....

[grid 개념정리](https://studiomeal.com/archives/533)

---

[오늘의 Chat] 

- grid는 신세계다..! float이나 flex에 비해 재밌게 느껴진다.
- 공부할 건 많은데.. 시간은 넉넉하지가 않다. 자꾸 쌓이기만 하고 있다 힝