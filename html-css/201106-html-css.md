## `[role="dialog"]`

스크린리더 사용자들에게 다이얼로그(대화상자)가 삽입되었다는 것을 안내하기 위해 사용할 수 있다. 이 다이얼로그는 일반적으로 오버레이를 사용하여 페이지 위에 표시된다. (오버레이해서 표현된 대화상자는 모달창이다.)

이때, 다이얼로그에 aria-labelledby로 컨테이너와 연결을 시켜주면, 마크업 구조가 인접하지 않고 떨어져 있어도 해당 대화상자가 어떤 내용과 연결되는지 설명을 제공할 수 있다. 

대화상자를 표시할 때에는 키보드 초점을 대화상자 내부로 옮겨야한다.

[참고 사이트](https://developer.mozilla.org/ko/docs/Web/Accessibility/ARIA/Roles/dialog_role)

## html `hidden`

전역 특성으로 해당 요소가 아직, 또는 더 이상 관련이 없음을 나타내는 불린(Boolean)값이다. hidden 속성을 설정한 요소는 렌더링되지 않는다.  (display: none;과 유사)

이디야 페이지 예제에서 커피 음료들의 리스트를 눌렀을 때 나오는 음료 디테일 모달창은 hidden 값을 갖고 있어 보이지 않다가 음료를 클릭했을 때 hidden 값이 사라지고 렌더링되어 화면에 보이게 된다. 

```html
<li class="ediya-menu__item">
   <a href="#" role="button" aria-haspopup="dialog" aria-pressed="false">
     <figure>
        <img src="../images/iced-cherry-blossoms-latte.png" alt width="323" height="323" />
        <figcaption>ICED 벚꽃라떼</figcaption>
     </figure>
   </a>
   <div hidden class="ediya-menu__item--detail" role="dialog" aria-modal="false" aria-labelledby=" ediya-menu__item1">
      <h3 id="ediya-menu__item1" class="ediya-menu__item--name">ICED 벚꽃라떼<span lang="en">Cherry Blossom Latte</span></h3>
      <p>은은한 벚꽃향과 라즈베리 화이트 초콜릿 토핑이 올라간 핑크빛 라떼</p>
      <button type="button" class="button is-close-panel" title="닫기" aria-label="음료 정보 패널 닫기">
        <span aria-hidden="true">×</span>
      </button>
   </div>
 </li>
```

## Multi-column

다단 레이아웃을 정의

column-count, column-rule 속성 등 다단 레이아웃을 할 전체 컨테이너에 선언해준다.  단락을 나누기 전 먼저 item들을 정렬하고 column을 부여하는 것이 좋다. column을 먼저 선언 후 안에 내용을 정렬하는 것이 좀더 까다롭다. 

- column-count : 몇 개의 컬럼으로 나눌지 설정
- column-gap : 컬럼 사이의 간격을 설정
- column-width : 컬럼의 너비
- column-rule : 컬럼 사이에 들어갈 라인의 두께(rule-width), 스타일(rule-style), 색상(rule-color)을 한꺼번에 지정
- column-span : 몇 개의 컬럼을 병합할지 설정
- column-fill : 컬럼을 어떻게 채울지 설정

## `<select>`

사용자가 선택할 수 있는 옵션 박스(드롭 다운되어서 고를수 있는)를 제공할 수 있다.

## 표 그리기 `<table>`

caption은 table 안에 오는 tag로 표의 설명에 쓰인다. 

`scope="col/row"` 를 이용하여 table의 각 셀에 대한 영역을 지정할 수 있다. 이를 통해 프로그램이 데이터를 읽어 내려가는 순서를 정할 수 있다. - th가 어떤 라인의 heading인지 나타낼 수 있음. colgroup / rowgroup값을 사용하여 제목들을 병합할 수도 있다.

`headers` 속성은 데이터 셀과 연결된 헤더 셀을 지정한다. 헤더셀의 id속성값을 데이터 셀의 headers 속성에 연결해주면 스크린리더 사용자들이 테이블의 정보를 읽어들이는 것이 수월해진다. headers에는 두 개의 값을 결합할 수도 있다.

## inline-block이 갖는 특징

마크업 상에서 줄바꿈이 된 inline-block들은 해당 줄바꿈(엔터)를 폰트 사이즈만큼의 글자폭으로 출력한다. 그렇기 때문에 스타일링상 이 공백을 없애려면 컨테이너(부모요소)에 font-size를 0으로 선언했다가 실제 텍스트를 가진 요소에 다시 font-size를 부여해줘야 한다. 

[참고블로그](https://didqk.tistory.com/entry/div-%EB%A5%BC-inline-block-%EC%9C%BC%EB%A1%9C-%ED%96%88%EC%9D%84-%EB%95%8C-%EC%83%9D%EA%B8%B0%EB%8A%94-%EA%B0%84%EA%B2%A9-%EC%97%AC%EB%B0%B1%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)

## etc,

- `figure` 는 button 요소 안에 올 수 없기 때문에 `a` 태그를 사용하여 버튼을 만들어준다. (role="button")
- 모달창? 팝업창?
`모달창` : 기존 브라우저 페이지 위에 레이어를 입혀 나타나는 창
`팝업창` : 현재 브라우저 페이지에 또다른 페이지 또는 탭을 연다.
- `aria-modal` 모달 스타일로 처리하는 경우 "true" 값을 넣어 속성 추가한다.
- `aria-live` 
페이지 중 일부를 '라이브'로 표시할 수 있다. 즉, 실시간으로 업데이트 되는 정보를 갱신하여 보여준다.
- `aria-current` 현재 페이지를 알려주며, 현재 맥락과 일치하는 항목을 의미한다.
- `aria-haspopup` 요소에 연결되어 있는 팝업 (메뉴, 대화상자) 정보를 제공한다.
- `aria-pressed` 토글 버튼이 눌린 상태를 표시한다.
- `Target / Container = Result` 반응형 계산 공식
- `<form>` 은 다이렉트로 꾸미기가 어려워서 div로 감싸주고 div를 꾸며준다.

