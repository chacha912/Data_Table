# 접근성 높은 표 만들기

## 표에 접근성이 필요한 이유
- 시각 장애인들은 눈으로 시각적인 표를 참고할 수 없기에 스크린 리더기를 통해 정보를 귀로 전달 받아야 한다.
<br>

- 만약 이때 접근성을 고려하지 않은 표를 마주친 경우 시각 장애인들은 혼자 힘으로 어떠한 정보도 제공 받을 수 없으며 이는 웹의 가장 큰 힘인 보편성을 잃게 된다.
<br>

- 따라서 소수일지라도 최대한 많은 사람이 접근할 수 있고 필요한 정보를 얻는데 차별이 없도록 콘텐츠를 제작해줘야 한다.

## 표에 사용 가능한 요소
- table 
    행과 열로 이루어진 표를 나타내는 요소
- caption
    표에 주제를 담는 요소
- colgroup
    표에서 열을 그룹화 해줄때 사용되는 요소
- col
    표에서 열을 의미하는 요소
- thead
    데이터가 담긴 표에서 제목을 나타내는 그룹 요소
- tbody
    표에 본문 행을 의미하는 요소
- tfoot
    표에 대략적인 결과 값을 담은 요소
- tr
    표에서 행을 지칭하는 요소
- th
    표에서 셀의 제목을 지칭
- td
    표에서 일반적인 셀을 지칭

## 표의 종류

<details>
<summary>열 혹은 행에 헤더가 한 줄인 경우</summary>

```html
<body>
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
</body>
```
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
</details>
<br>
<details>
<summary>열과 행 양측에 헤더가 있는 경우</summary>

```html
<body>
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
    </table>
</body>
```
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
    </table>
</details>
<br>
<details>
<summary>불규칙하게 해더가 존재하는 경우</summary>

```html
<body>
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
</body>
```
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
</details>
<br>
<details>
<summary>헤더가 같은 행 혹은 열에 주기적으로 반복되는 경우</summary>

```html
<body>
    <table>
  <caption>
    Supplier contacts
  </caption>
  <tr>
    <th id="blank">&nbsp;</th>
    <th id="co1" headers="blank">Example 1 Ltd</th>
    <th id="co2" headers="blank">Example 2 Co</th>
  </tr>
  <tr>
    <th id="c1" headers="blank">Contact</th>
    <td headers="co1 c1">James Phillips</td>
    <td headers="co2 c1">Marie Beauchamp</td>
  </tr>
  <tr>
    <th id="p1"  headers="blank">Position</th>
    <td headers="co1 p1">Sales Director</td>
    <td headers="co2 p1">Sales Manager</td>
  </tr>
  <tr>
    <th id="e1"  headers="blank">Email</th>
    <td headers="co1 e1">jp@1ltd.example.com</td>
    <td headers="co2 e1">marie@2co.example.com</td>
  </tr>
  <tr>
    <th>&nbsp;</th>
    <th id="co3" headers="blank">Example 3 Ltd</th>
    <th id="co4" headers="blank">Example 4 Inc</th>
  </tr>
  <tr>
    <th id="c2"  headers="blank">Contact</th>
    <td headers="co3 c2">Suzette Jones</td>
    <td headers="co4 c2">Alex Howe</td>
  </tr>
  <tr>
    <th id="p2" headers="blank">Position</th>
    <td headers="co3 p2">Sales Officer</td>
    <td headers="co4 p2">Sales Director</td>
  </tr>
  <tr>
    <th id="e2" headers="blank">Email</th>
    <td headers="co3 e2">Suz@ltd3.example.com</td>
    <td headers="co4 e2">howe@4inc.example.com</td>
  </tr>
</table>
</body>
```
<table>
  <caption>
    Supplier contacts
  </caption>
  <tr>
    <th id="blank">&nbsp;</th>
    <th id="co1" headers="blank">Example 1 Ltd</th>
    <th id="co2" headers="blank">Example 2 Co</th>
  </tr>
  <tr>
    <th id="c1" headers="blank">Contact</th>
    <td headers="co1 c1">James Phillips</td>
    <td headers="co2 c1">Marie Beauchamp</td>
  </tr>
  <tr>
    <th id="p1"  headers="blank">Position</th>
    <td headers="co1 p1">Sales Director</td>
    <td headers="co2 p1">Sales Manager</td>
  </tr>
  <tr>
    <th id="e1"  headers="blank">Email</th>
    <td headers="co1 e1">jp@1ltd.example.com</td>
    <td headers="co2 e1">marie@2co.example.com</td>
  </tr>
  <tr>
    <th>&nbsp;</th>
    <th id="co3" headers="blank">Example 3 Ltd</th>
    <th id="co4" headers="blank">Example 4 Inc</th>
  </tr>
  <tr>
    <th id="c2"  headers="blank">Contact</th>
    <td headers="co3 c2">Suzette Jones</td>
    <td headers="co4 c2">Alex Howe</td>
  </tr>
  <tr>
    <th id="p2" headers="blank">Position</th>
    <td headers="co3 p2">Sales Officer</td>
    <td headers="co4 p2">Sales Director</td>
  </tr>
  <tr>
    <th id="e2" headers="blank">Email</th>
    <td headers="co3 e2">Suz@ltd3.example.com</td>
    <td headers="co4 e2">howe@4inc.example.com</td>
  </tr>
</table>
</details>

## 표 접근성 고려 요소
- 알맞은 scope선택을 통해 각 셀이 어떠한 내용을 담고 있는지 명시
<br>

- tfoot을 tbody보다 우선적으로 줄 시 모든 셀을 확인하기 이전 tfoot을 통해 대략적인 결과 데이터를 알 수 있어 시간 단축 가능
<br>

- 내용이 없는 셀을 마주친다면 값을 "없음"등과 비슷하게 명확하게 넣어주고 CSS를 통해 숨김 처리를 해주면 디자인상의 문제 없이 접근성 향상이 가능
<br>

- 표의 목적에 대한 명확하고 상세한 설명을 caption에 삽입하여 표 콘텐츠에 대한 정보 및 열람에 대한 선택권을 줄 수 있음

<details>

<summary>참고자료</summary>
<a href="https://developer.mozilla.org/en-US/">MDN</a>
<br>
<a href="https://seulbinim.github.io/WSA/table.html#table-tr-th-td-%EC%9A%94%EC%86%8C">강사님 깃헙 정리글</a>
<br>
<a href="https://www.w3.org/WAI/tutorials/tables/">W3C 접근성 튜토리얼</a>
</details>