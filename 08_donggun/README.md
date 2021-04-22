# 접근성 높은 표 만들기

## 우선 표에 접근성이 필요한 이유!
- 시각 장애인들은 눈으로 시각적인 표를 참고할 수 없기에 스크린 리더기를 통해 정보를 귀로 전달 받아야 한다.   
<br>

- 만약 이때 접근성을 고려하지 않은 표를 마주친 경우 시각 장애인들은 혼자 힘으로 어떠한 정보도 제공 받을 수 없으며 이는 웹의 가장 큰 힘인 보편성을 잃게 된다.
<br>

- 따라서 소수일지라도 최대한 많은 사람이 접근할 수 있고 필요한 정보를 얻는데 차별이 없도록 콘텐츠를 제작해줘야 한다.

# 표와 관련된 요소 및 접근성 고려사항
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
<summary>열 혹은 행에 헤더가 한 줄인 경우<summary>

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
</details>

## 표 접근성 고려 요소
- 알맞은 scope선택을 통해 각 셀이 어떠한 내용을 담고 있는지 명시
<br>
- tfoot을 tbody보다 우선적으로 줄 시 모든 셀을 확인하기 이전 tfoot을 통해 대략적인 결과 데이터를 알 수 있어 시간 단축 가능
<br>
- 내용이 없는 셀을 마주친다면 값을 "없음"등과 비슷하게 명확하게 넣어주고 CSS를 통해 숨김 처리를 해주면 디자인상의 문제 없이 접근성 향상이 가능
<br>
- 표의 목적에 대한 명확하고 상세한 설명을 caption에 삽입하여 표 콘텐츠에 대한 정보 및 열람에 대한 선택권을 줄 수 있음