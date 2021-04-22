# HTML table study & 인터넷우체국 요금안내([링크](https://parcel.epost.go.kr/parcel/use_guide/charge_1.jsp)) 테이블 마크업 실습

> draft by 허재혁
> created at 210422

## table 개요

> HTML table 개요는 김데레사님의 github 페이지 중 [테이블 관련 요소](https://seulbinim.github.io/WSA/table.html#caption-%EC%9A%94%EC%86%8C)를 참고하고 [W3 table tutorial](https://www.w3.org/WAI/tutorials/tables/)을 함께 비교하며 정리하였다.

### tr, th, td 요소

- **tr**: table row 요소로서 테이블의 행을 의미한다.
- **th**: table head 요소로서 데이터 테이블의 제목 셀을 의미하며, 이는 데이터 테이블의 필드에 해당한다.
- 이때 th 요소에 scope 속성을 사용하여 해당 셀이 영향을 주는 내용 셀의 범위를 지정할 수 있다. 예를 들어 th 요소로 마크업한 셀이 동일한 열(세로)에 있는 내용 셀과 연관성이 있는 경우 scope="col", 동일한 행에 있는 내용 셀과 연관성이 있는 경우 scope="row" 형식으로 지정할 수 있다.
- **td**: table data 요소로서 테이블의 내용셀을 의미한다. HTML5에는 td 요소는 섹셔닝 루트 요소이기 때문에 td 요소 안에 제목 등을 사용하였다고 하더라도 독립된 콘텐츠로 인식되어 아웃라인에 영향을 주지 않는다.
- 만약 특정 셀을 병합하고자 할 때 병합하고자 하는 방향에 따라 열이 다른 셀을 병합할 때는 colspan 속성을, 행이 서로 다른 셀을 병합할 때는 rowspan 속성을 사용할 수 있다.

### caption, summary 요소

- **caption**: caption 요소는 table 요소에 제목이나 설명을 마크업할 때 사용하는 요소이다. caption 요소는 table 요소 안에서 가장 먼저 마크업해야 하며, 필수 요소는 아니다.
  - HTML5에 신규 추고된 figure 안에 마크업할 경우, figcaption이 caption의 역할을 대신하도록 할 수 있다.
- **summary**: summary 요소는 table 내용을 요약한 내용으로 이는 HTML5 규격에서 제외되었다.
  - 요약 정보의 경우 summary 속성을 사용하여 제공할 수 있는데 해당 요약 정보를 통해 스크린 리더 사용자는 테이블의 정보를 다 듣지 않아도 어떤 내용이 포함되어 있는지 파악가능하다. HTML5 문서 형식에 맞게 요약 정보를 제공하고자 할 때는 새롭게 추가된 figure, figcaption 요소를 사용하거나 aria-describedby으로 요약 정보를 제공하고 있는 단락을 연결하거나 caption 요소 내에 포함하여 제공할 수 있다.

### colgroup, col 요소

- **col**: col 요소는 테이블의 열 그룹을 의미한다. colgroup 요소를 사용하여 2개 이상의 열을 그룹화한 경우 span 속성(attribute)을 사용할 수 있다. 이때 span="2"는 2개의 열을 그룹화했음을 의미하여, colgroup 요소의 자식 요소로 col 요소를 사용하여 2개의 열이 각각 어떤 의미를 가지는지에 대한 의미를 부여하고 특정 열에 스타일을 지정할 수 있다. caption 요소 **다음**에 마크업해야 하며, thead, tbody, tfoot 요소보다 **이전**에 마크업해야 한다.

- **colgroup**: colgroup 요소는 테이블의 컬럼(td 태그)에 적용할 스타일 width와 background를 해당 태그에서 미리 적용할 수 있게 한다. 그러나 HTML5에서는 공식적으로 지원하지 않는다. 마크업에서는 가급적 시멘틱한 구조만 구성하는 것이 바람직해 보인다.

### thead, tbody, tfoot 요소

thead, tbody, tfoot 요소는 테이블의 **행 그룹**을 의미한다.

- **thead**: 데이터 테이블의 제목 셀 그룹을 의미한다. table 요소 내에서 한 번만 사용가능하다.
- **tbody**: 테이블의 본문 행을 의미하며, table 요소의 필수 요소입니다. 그러나 tbody 요소를 생략하더라도 대다수의 웹 브라우저에서 tbody 요소가 있는 것으로 가정하고 DOM을 구성한다.
- **tfoot**: 레코드 내용의 소계나 합계 등의 정보에 해당하는 푸터행을 의미한다. table 요소 내에서 한 번만 사용가능하다.
- 렌더링: 마크업 시 thead, tbody, tfoot 또는 thead, tfoot, tbody 순서로 작성할 수 있으며, 두 가지 경우 모두 tfoot 요소가 가장 마지막에 렌더링된다.

> thead, tfoot 요소의 장점
> table 마크업 시 thead와 tfoot이 없어도 구성가능하다. 그럼에도 불구하고 thead와 tfoot 요소를 사용하는 이유는 다음과 같다.
>
> 1. 웹 브라우저에 따라 테이블의 데이터가 매우 많기 때문에 인쇄할 때 여러 장에 걸쳐 출력되는 경우 페이지마다 테이블의 thead, tfoot 정보를 인쇄할 수 있다.
> 1. thead 요소 다음에 tfoot 요소의 정보가 위치하여 순차적으로 콘텐츠에 접근하는 시각 장애인의 경우에 점수 통계 및 등수와 같은 테이블 종합 정보를 일일이 모든 셀의 데이터를 읽지 않다도 먼저 알 수 있다.
>    _결론_: 2번의 이유처럼 시각 장애인의 웹 접근성을 향상시키는 것이 1번과 같은 일반인의 웹 접근성 내지 편리함을 가져다 줄 수 있음을 발견할 수 있다.

### scope, id, headers 속성

일반 사용자의 경우 웹 브라우저에 나타나는 테이블 데이터를 열과 행, 그리고 셀로 구별하는 것은 어렵지 않다. 하지만 시각 장애가 있는 사용자나 화면 낭독기의 경우 왼쪽에서 오른쪽으로 셀의 내용만 듣거나 읽어 판단하기 때문에 열과 행을 파악하고 내용 셀의 연관성을 유추하는 것이 쉽지 않다. 이러한 문제를 해결하기 위해 th 요소에 scope 속성을 추가할 것을 권장한다.

th 요소에 scope 속성을 지정하고 해당 값으로 col이나 row, rowgroup, colgroup을 할당하면 해당 셀이 열의 제목인지, 행의 제목인지를 알 수 있다.

scope 속성의 경우 주로 병합되지 않은 단순한 형태의 테이블 유형에 사용할 수 있다. 그리고 좀 더 복잡하게 병합된 셀의 경우, th 요소는 id 속성으로 네이밍을 하고 해당 제목 셀과 연관성이 있는 내용 셀에 headers 속성값에 id 값을 연결하여 제목 셀과 내용 셀의 관계를 지정할 수 있다.

_적용 예_

```html

<!-- scope 속성의 사용 -->
<table border="1">
    <tr>
        <th scope="col">열 제목</th>
        <th scope="col">열 제목</th>
        <th scope="col">열 제목</th>
    </tr>
    <tr>
        <th scope="row">행 제목</th>
        <td>내용 셀</td>
        <td>내용 셀</td>
    </tr>
    </table>

<!-- id, headers 속성의 사용 -->
<table>
    <tr>
        <th>&nbsp;</th>
        <th id="imported" colspan="2">수입품목</td>
    </tr>
    <tr>
        <th>&nbsp;</th>
        <th id="cosmetic">화장품</td>
        <th id="car">자동차</td>
    </tr>
    <tr>
        <th id="america">미국</th>
        <td headers="imported cosmetic america">7000</td>
        <td headers="imported car america">30</td>
    </tr>
    <tr>
        <th id="japan">일본</th>
        <td headers="imported cosmetic japan">5000</td>
        <td headers="imported car japan">80</td>
    </tr>
</table>
```

> Table 내의 내용 없는 셀(td) 표현
> 값이 없거나 0인 경우에는 아무것도 없는 <td></td>와 같이 빈 셀로 표현하는 경우가 있는데 이 경우 CSS에서 `border-collapse: collapse`를 사용하지 않는 경우 설정한 border가 제대로 표현되지 않을 수 있으며, 스크린 리더를 사용할 경우 내용 없는 빈 셀은 테이블의 구조를 파악하기 어렵게 만든다. 이 경우에는 값을 사용하여 빈 데이터를 넣거나 값이 없는 경우는 '없음'과 같은 텍스트를 삽입한 후 CSS를 사용하여 텍스트를 숨겨서 제공하면 디자인상의 문제없이 table의 정보 접근성을 향상할 수 있다.
