# Web Accessibility(웹 접근성)
## 개요
### 웹 접근성
- 웹 접근성은 장애를 가진 사람과 장애를 가지지 않은 사람(모바일 장치를 사용하는 사람, 느린 네트워크 연결을 사용하는 사람 등) 모두가 웹사이트를 이용할 수 있게 하는 방식을 말한다.

### 웹 브라우징에 쓰이는 보조과학기술
- 스크린 리더
- 화면 확대 도구
- 음성 인식
- 키보드 오버레이

## Guide of Web Accessibility
`
W3C의 Web Accessibility Tutorials에 나와있는 대표적인 주제들은 다음과 같으며 테이블에 대해 집중적으로 살펴보자.
`
### Page Structure
- [Page Regions](https://www.w3.org/WAI/tutorials/page-structure/regions/)
- [Labeling Regions](https://www.w3.org/WAI/tutorials/page-structure/labels/)
- [Headings](https://www.w3.org/WAI/tutorials/page-structure/headings/)
- [Content Structure](https://www.w3.org/WAI/tutorials/page-structure/content/)

### Menu
- [Structure](https://www.w3.org/WAI/tutorials/menus/structure/)
- [Styling](https://www.w3.org/WAI/tutorials/menus/styling/)
- [Fly-out Menus](https://www.w3.org/WAI/tutorials/menus/flyout/)
- [Application Menus](https://www.w3.org/WAI/tutorials/menus/application-menus/)

### Images
- [Informative Images](https://www.w3.org/WAI/tutorials/images/informative/)
- [Decorative Images](https://www.w3.org/WAI/tutorials/images/decorative/)
- [Functional Images](https://www.w3.org/WAI/tutorials/images/functional/)

### Form
- [Labeling Controls](https://www.w3.org/WAI/tutorials/forms/labels/)
- [Grouping Controls](https://www.w3.org/WAI/tutorials/forms/grouping/)
- [Form Instructions](https://www.w3.org/WAI/tutorials/forms/instructions/)

### Table
- [One Header](https://www.w3.org/WAI/tutorials/tables/one-header/)
    - [헤더 셀이 첫 행에만 있는 경우](#헤더-셀이-첫-행에만-있는-경우)
    - [헤더 셀이 첫 열에만 있는 경우](#헤더-셀이-첫-열에만-있는-경우)
    - [데이터 구분이 모호한 경우](#데이터-구분이-모호한-경우)
- [Two Header](https://www.w3.org/WAI/tutorials/tables/two-headers/)
    - [맨 위 행과 첫 번째 열에 헤더 셀이 있는 테이블](#맨-위-행과-첫-번째-열에-헤더-셀이-있는-테이블)
    - [헤더 셀에 오프셋 열이 있는 테이블](#헤더-셀에-오프셋-열이-있는-테이블)
- [Irregular Header](https://www.w3.org/WAI/tutorials/tables/irregular/)
    - [두 개의 계층 헤더가 있는 테이블](#두-개의-계층-헤더가-있는-테이블)
    - [여러 행 또는 열에 걸쳐 헤더가 있는 테이블](#여러-행-또는-열에-걸쳐-헤더가-있는-테이블)
- [Multi-level Headers](https://www.w3.org/WAI/tutorials/tables/multi-level/)
    - [multi-level 헤더를 가진 테이블](multi-level-헤더를-가진-테이블)
- [Caption & Summary](https://www.w3.org/WAI/tutorials/tables/caption-summary/)
    - [caption을 사용한 테이블 식별](#caption을-사용한-테이블-식별)
    - [보다 복잡한 테이블에 대한 summary](#보다-복잡한-테이블에-대한-summary)


# Web Accessibility of Table

> 헤더와 셀을 구별, 연결하는 구조적 표시가 없는 테이블은 접근성 장벽을 만든다. 시각적 단서만으로는 충분하지 않으며 구조 마크업을 사용해야 한다. 

## Header가 하나 있는 테이블
- 행에 대한 하나의 단순 헤더 또는 열에 대한 하나의 단순 헤더가 있는 테이블에 대한 내용이며 이러한 테이블의 데이터는 그 자체로 설명되며 명확한 의미를 가지고 있다.

### 헤더 셀이 첫 행에만 있는 경우
- 다음 테이블은 첫 번째 행의 셀을 `<th>`요소로 표시한다. 이 경우는 매우 작은 테이블이고 헤더와 데이터 셀의 관계가 명백하기 때문에 허용된다.
```html
<table>
  <tr>
    <th>Date</th>
    <th>Event</th>
    <th>Venue</th>
  </tr>
  <tr>
    <td>12 February</td>
    <td>Waltz with Strauss</td>
    <td>Main Hall</td>
  </tr>
  […]
</table>
```

### 헤더 셀이 첫 열에만 있는 경우
- 첫 행에만 있는 경우와 마찬가지로 테이블이 작기 때문에 다음 코드를 사용하는 것만이 허용된다.
```html
<table>
  <tr>
    <th>Date</th>
    <td>12 February</td>
    <td>24 March</td>
    <td>14 April</td>
  </tr>
  <tr>
    <th>Event</th>
    <td>Waltz with Strauss</td>
    <td>The Obelisks</td>
    <td>The What</td>
  </tr>
</table>
```

### 데이터 구분이 모호한 경우
- 아래 예에서는 데이터(이름, 성, 도시)를 서로 구분하지 않고는 각 헤더를 구분할 수 없다. `col`값이 있는 `scope`속성은 헤더 셀의 방향을 정의하고 해당 데이터 셀과 연결한다.
- `scope`속성은 헤더 행 또는 열이 하나 있는 큰 테이블에도 필요하다.

```html
<table>
  <caption>Teddy bear collectors:</caption>
  <tr>
    <th scope="col">Last Name</th>
    <th scope="col">First Name</th>
    <th scope="col">City</th>
  </tr>
  <tr>
    <td>Phoenix</td>
    <td>Imari</td>
    <td>Henry</td>
  </tr>
  <tr>
    <td>Zeki</td>
    <td>Rome</td>
    <td>Min</td>
  </tr>
  <tr>
    <td>Apirka</td>
    <td>Kelly</td>
    <td>Brynn</td>
  </tr>
</table>
```
---
## Header가 2개 있는 테이블
- 각각 하나의 row header, column header를 가진 경우 데이터와 셀의 관계는 모호해진다. 이러한 경우, Header Cell을 식별하기 위해 `<th>`를 사용하고 각 헤더의 방향을 선헌하기 위한 `scope`속성을 사용한다.
- `<caption>`을 사용하여 문서의 테이블을 식별할 수 있다. 이것은 특히 사용자가 테이블에서 테이블로 이동할 수 있는 '테이블 모드'에서 웹 페이지를 검색하는 스크린리더 사용자에게 유용하다.

### 맨 위 행과 첫 번째 열에 헤더 셀이 있는 테이블
- 모든 헤더 셀은 `<th>`과 `scope`을 가지고 있다.
- 헤더 행에서 범위에 대한 `col`값은 각 헤더 셀을 해당 열의 데이터와 연결한다.
```html
<table>
  <caption>Delivery slots:</caption>
  <tr>
    <td></td>
    <th scope="col">Monday</th>
    <th scope="col">Tuesday</th>
    <th scope="col">Wednesday</th>
    <th scope="col">Thursday</th>
    <th scope="col">Friday</th>
  </tr>
  <tr>
    <th scope="row">09:00 - 11:00</th>
    <td>Closed</td>
    <td>Open</td>
    <td>Open</td>
    <td>Closed</td>
    <td>Closed</td>
  </tr>
  <tr>
    <th scope="row">11:00 - 13:00</th>
    <td>Open</td>
    <td>Open</td>
    <td>Closed</td>
    <td>Closed</td>
    <td>Closed</td>
  </tr>
  […]
</table>
```

### 헤더 셀에 오프셋 열이 있는 테이블
- 헤더 셀에 오프셋 열이 있으면 row 헤더 셀은 두번째 열에 존재한다. 
- `row`속성을 통해 연관지어준다.
```html
[…]
<tr>
  <td>215</td>
  <th scope="row">Abel</th>
  <td>5</td>
  <td>2</td>
  <td>0</td>
</tr>
[…]
```

## 헤더가 불규칙한 테이블
- 여러 열 또는 행에 걸쳐 있는 헤더 셀이 있는 테이블에 관한 규칙이다. 
- 예를 들어, 세개의 열에 걸쳐 있는 헤더 셀은 열 그룹의 해당 데이터 셀과 연관되어야 한다. 헤더 셀의 `scope`을 `colgroup`으로 설정하여 이 작업을 진행할 수 있다. 동일한 원리가 여러 행에 걸쳐 있는 헤더 셀에도 적용된다. 이 경우 `scope`을 `rowgroup`으로 설정하여 연결한다.
- 그러나 이러한 연결을 만들기 전에 다음과 같이 열 및 행 그룹의 구조를 테이블 마크업에서 정의해야 한다.
    - column group은 `<colgroup>`요소를 사용하여 정의된다.
    - row group은 `<thead>`, `<tfoot>`, `<tbody>` 요소로 정의된다.
        - `<thead>`, `<tfoot>`은 테이블에서 한 번 사용할 수 있다.
        - 테이블에는 행 그룹을 정의하는 여러개의 `<tbody>`요소가 있을 수 있다.



### 두 개의 계층 헤더가 있는 테이블
- 아래 테이블에는 두 쌍의 column header가 있다. 각 column header의 쌍은 첫 번째 헤더 "Produced"와 "Sold"에 연관된다. 첫번째 헤더는 값이 2인 `colspan` 속성을 사용하여 두 열에 걸쳐 작성된다.
- 첫 번째 헤더를 두 열의 모든 셀과 올바르게 연결하려면 표의 시작 부분에 열 구조를 정의해야 한다. `<col>`요소는 왼쪽에서 시작하여 각 열을 식별한다. 헤더가 두 개이상의 열에 걸쳐 있는 경우 해당 수의 `<col>`요소 대신 `<colgroup>` 요소를 사용하고, 확장된 열의 수는 `<span>`속성에 표시된다.
- 또한 첫 헤더의 범위 속성 값은 전체 열 그룹과 연결되도록 `colgroup`으로 설정된다. 두 번째 레벨의 헤더는 해당 열에만 적용되므로 스코프 속성은 이전 예에 표시된대로 설정된다.

```html
<table>
  <col>
  <colgroup span="2"></colgroup>
  <colgroup span="2"></colgroup>
  <tr>
    <td rowspan="2"></td>
    <th colspan="2" scope="colgroup">Mars</th>
    <th colspan="2" scope="colgroup">Venus</th>
  </tr>
  <tr>
    <th scope="col">Produced</th>
    <th scope="col">Sold</th>
    <th scope="col">Produced</th>
    <th scope="col">Sold</th>
  </tr>
  <tr>
    <th scope="row">Teddy Bears</th>
    <td>50,000</td>
    <td>30,000</td>
    <td>100,000</td>
    <td>80,000</td>
  </tr>
  <tr>
    <th scope="row">Board Games</th>
    <td>10,000</td>
    <td>5,000</td>
    <td>12,000</td>
    <td>9,000</td>
  </tr>
</table>
```

### 여러 행 또는 열에 걸쳐 헤더가 있는 테이블
- 아래 예제에서 표는 세 열에 걸쳐 있는 두개의 개별 열과 하나의 열 그룹으로 구성된다. 총 6개의 열을 가지고 있다. 여러 행에 걸쳐 있는 두 개의 헤더 셀이 해당 행의 모든 셀과 올바르게 연결되었는지 확인하려면 행을 그룹화해야 한다. 행 그룹을 정의하려면 해당 행을 `<tbody>`로 설정한다. 또한 행에 걸쳐 있는 헤더 셀의 범위 속성은 `<colgroup>`으로 설정되어야 한다.
- 헤더가 여러 헤더 행에 걸쳐 있는 경우, 행을 `<tbody>`요소 대신 `<thead>`요소로 줄바꿈한다. 머리글이 표의 바닥글 영역에서 여러 행에 걸쳐 있는 경우 `<tfoot>`요소를 사용한다.
- 표의 복잡성으로 인해 `summary`을 사용하여 표의 레이아웃을 자세히 설명할 수 있습니다.

```html
<table>
  <caption>
    Poster availability
  </caption>
  <col>
  <col>
  <colgroup span="3"></colgroup>
  <thead>
    <tr>
      <th scope="col">Poster name</th>
      <th scope="col">Color</th>
      <th colspan="3" scope="colgroup">Sizes available</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" scope="rowgroup">Zodiac</th>
      <th scope="row">Full color</th>
      <td>A2</td>
      <td>A3</td>
      <td>A4</td>
    </tr>
    <tr>
      <th scope="row">Black and white</th>
      <td>A1</td>
      <td>A2</td>
      <td>A3</td>
    </tr>
    <tr>
      <th scope="row">Sepia</th>
      <td>A3</td>
      <td>A4</td>
      <td>A5</td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <th rowspan="2" scope="rowgroup">Angels</th>
      <th scope="row">Black and white</th>
      <td>A1</td>
      <td>A3</td>
      <td>A4</td>
    </tr>
    <tr>
      <th scope="row">Sepia</th>
      <td>A2</td>
      <td>A3</td>
      <td>A5</td>
    </tr>
  </tbody>
</table>
```

## multi-level 헤더를 가진 테이블

- 데이터 셀당 연결된 multi-level 헤더 셀이 있는 테이블은 복잡하여 헤더와 데이터 셀 사이의 엄격한 수평 또는 수직 연관성을 식별하기 어렵다. 이러한 테이블에서 각 테이블 헤더는 고유 `id`로 표시된다. 데이터 셀은 `headers` 속성에 하나 이상의 `id`를 공백으로 구분하여 나열해 해당 ID를 나타낸다.
- 머리글이 여러 개인 테이블에는 해당 테이블을 식별하는 `caption`과 `summary`가 존재해야 할 수도 있다.

```html
[…]
<td id="blank">&nbsp;</td>
<th id="co1" headers="blank">Example 1 Ltd</th>
<th id="co2" headers="blank">Example 2 Co</th>
[…]
<th id="c1" headers="blank">Contact</th>
[…]
<td headers="co1 c1">James Phillips</td>
<td headers="co2 c1">Marie Beauchamp</td>
[…]
```

## Caption & Summary

- caption과 summary 사용자가 표를 찾고, 탐색하고, 이해하는데 도움이 되는 정보를 제공한다. 모든 경우 WCAG를 충족하는 데 필요한 것은 아니지만, Caption과 Summary는 종종 필요한 정보를 제공하는 매우 간단한 방법이다.
    - WCAG(Web Content Accessibility Guidelines): 웹 콘텐츠 접근성 지침

- caption은 테이블의 제목과 같은 기능을 한다. 대부분의 스크린 리더는 caption 내용을 표시한다. caption을 사용하면 테이블을 찾고 이해하며 테이블을 읽을지 여부를 결정할 수 있다. 사용자가 "테이블 모드"를 사용하는 경우 caption이 테이블을 식별하는 기본 매커니즘이다. caption은 `<caption>`요소에 의해 제공된다.

- summary는 테이블에서 데이터의 구성에 대한 정보를 전달하고 사용자가 데이터를 탐색하는 데 도움이 된다. 예를 들어, 테이블의 구조가 특이할 경우 사용자에게 제공할 수 있는 행 또는 열에서 찾을 수 있는 내용에 대한 정보이다. 일반적으로 summary는 복잡한 테이블에만 필요하다.

- 한 테이블에 대해 caption과 summary가 모두 제공되는 경우, summary는 caption에 있는 정보를 복제하지 않아야 한다.


### caption을 사용한 테이블 식별
- caption은 테이블 내용에 대한 짧은 제목이어야 한다. 
- `<caption>` 요소는 `<table>`요소의 하위 요소로 직접 배치된다.

### 보다 복잡한 테이블에 대한 summary
- 방법 1: `<caption>` 요소 내부에 중첩 요약
    아래 예시는 두 개의 개별 위치에서 서로 다른 유형과 크기의 숙박 시설을 이용할 수 있음을 보여준다. `<caption>` 요소는 표의 머리글 역할을 하며 표의 구성도 설명하는 요약을 제공한다.

```html
<caption>Availability of holiday accommodation <br>
  <span>Column one has the location and size of accommodation, other columns show the type and number of properties available</span>
</caption>
```

- 방법 2: `aria-describedby`를 지공하여 테이블 summary 제공
    - 이 접근법에서 `id`속성을 가진 요소는 표의 `aria-describedby`를 사용하여 요약과 연관지을 수 있다. 고유한 `id`속성을 가진 모든 요소를 이 방법으로 테이블에 대한 summary로 사용할 수 있다.
    - summary가 포함된 요소는 문서의 테이블 앞에 있을 필요는 없지만 요약이 테이블 근처에 있는 경우, 특히 스크린 리더를 화면하지 않는 경우 사용자가 요약을 더 빨리 검색할 수 있도록 도와준다.
    - 하지만, 이 WAI-ARIA 기능은 summary에 대한 다른 접근 방식보다 보조 기술에 의해 널리 지원되지 않을 수 있다.
```html
<p id="tblDesc">Column one has the location and size of accommodation, other columns show the type and number of properties available.</p>
<table aria-describedby="tblDesc">
[…]
```

- 방법 3: `<figure>`요소를 사용하여 summary 표시
    - 이 접근법에서 테이블은 `<figure>`요소로 감싸진다. `<figcaption>`요소에는 caption과 summary 내용이 포함되어 있다.
    - 표 모드에서 탐색하는 스크린 리더 사용자는 일반적으로 이와 같은 캡션을 적용하여 표를 식별할 수 없다. `<figcaption>`요소의 caption 부분은 `aria-labbelledby`속성을 사용해 테이블에 명시적으로 연결할 수 있고 `aria-labbelledby`속성을 사용해 summary 부분을 사용할 수 있다. 이렇게 하면 caption과 summary가 여러 번 읽힐 수 있다.
    - 하지만, 이 HTML5 기능은 summary에 대한 다른 접근 방식보다 보조 기술에 의해 널리 지원되지 않을 수 있다.

```html
<figure>
  <figcaption>
    <strong id="paris-caption">Paris: Availability of holiday accommodation</strong><br>
    <span id="paris-summary">Column one has the location and size of accommodation, other columns show the type and number of properties available.</span>
  </figcaption>
  <table aria-labelledby="paris-caption" aria-describedby="paris-summary">
[…]
  </table>
</figure>
```

- 방법 4: `summary`속성을 사용
    - 해당 접근법에서 요약 텍스트는 표의 `summary`속성 안에 있다. 이러한 요약은 시각적으로 표시되지 않고, 일반적으로 스크린 리더 사용자만 사용할 수 있다.
    - 하지만, `summary` 속성은 HTML5에서 더 이상 사용되지 않는다.

```html
<table
  summary="Column one has the location and size of accommodation, other columns show the type and number of properties available.">
```
