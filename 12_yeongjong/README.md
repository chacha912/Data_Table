# 우체국 요금안내 페이지의 테이블 만들어보기
[우체국 요금안내 페이지](https://parcel.epost.go.kr/parcel/use_guide/charge_1.jsp)

우체국 홈페이지의 요금안내 페이지를 들어가보면 5개의 테이블로 요금정보를 제공하고 있습니다.

이 테이블들을 만들어보며, 고려해야할 부분을 학습하고 정리해 보겠습니다.

# 첫번째 테이블
## 첫번째 시도
참조하지 않고 만들어보기

### 결과
<table class="price-table">
	<tr>
		<th colspan="2">구분<br>(초과 ~ 이하)</th>
		<th>5kg 이하<br>(80㎝ 이하)</th>
		<th>5kg∼10kg<br>(80㎝∼100㎝)</th>
		<th>10kg∼20kg<br>(100㎝∼120㎝)</th>
		<th>20kg∼30kg<br>(120㎝∼160㎝)</th>
	</tr>
	<tr>
		<th colspan="2">익일배달</th>
		<td>5,000</td>
		<td>8,000</td>
		<td>10,000</td>
		<td>12,000</td>
	</tr>
	<tr>
		<th rowspan="2">제주</th>
		<th>익일배달</th>
		<td>7,500</td>
		<td>10,500</td>
		<td>12,500</td>
		<td>14,500</td>
	</tr>
	<tr>
		<th>D+2 배달</th>
		<td>5,000</td>
		<td>8,000</td>
		<td>10,000</td>
		<td>12,000</td>
	</tr>
</table>

```
<table class="price-table">
	<tr>
		<th colspan="2">구분<br>(초과 ~ 이하)</th>
		<th>5kg 이하<br>(80㎝ 이하)</th>
		<th>5kg∼10kg<br>(80㎝∼100㎝))</th>
		<th>10kg∼20kg<br>(100㎝∼120㎝)</th>
		<th>20kg∼30kg<br>(120㎝∼160㎝)</th>
	</tr>
	<tr>
		<th colspan="2">익일배달</th>
		<td>5,000</td>
		<td>8,000</td>
		<td>10,000</td>
		<td>12,000</td>
	</tr>
	<tr>
		<th rowspan="2">제주</th>
		<th>익일배달</th>
		<td>7,500</td>
		<td>10,500</td>
		<td>12,500</td>
		<td>14,500</td>
	</tr>
	<tr>
		<th>D+2 배달</th>
		<td>5,000</td>
		<td>8,000</td>
		<td>10,000</td>
		<td>12,000</td>
	</tr>
</table>
```
## 두번째 시도
MDN 문서를 읽고 작성해보기.

### Caption
표의 목적에 대해 명확하고 상세한 설명을 포함하는 caption 요소를 제공하는 것이 유저가 표 콘텐츠를 확인할지, 넘어갈지 결정하는데 큰 도움을 준다고 합니다. HTML5와 HTML4.01에서 사용하길 적극 권장하는 caption을 사용해 표를 설명하는 요소를 삽입해 보겠습니다.

**note: \<table> 요소의 첫 번쨰 자식이어야 한다.**

### Scoping rows and columns

어떻게 보면 당연하지만 table 정보를 파악하기 위해 header와 cell의 관계를 인지하는 것은 매우 중요합니다.

이런 관계를 파악하기 힘든 사용자가 있습니다. 스크린리더기를 통해 정보를 얻는 사용자의 경우 테이블 내의 header를 cell(데이터)과 함께 읽어주어야 그 관계를 파악할 수 있습니다. 하지만 일반적으로 왼쪽에서 부터 오른쪽으로 읽어 나가는 방식의 보조기기는 상단의 헤더를 먼저 읽은 후에 나머지 셀을 순차적으로 모두 읽어 내려가는 방식이기 때문에 각 셀이 어떤 헤더에 해당하는지 파악하기 어렵습니다. 이런 문제점을 개선하기 위해서 Scope 속성을 삽입할 수 있습니다.

### 결과

<h2>우체국택배(방문접수)</h2>
	<table class="price-table">
		<caption>고객이 원하는 장소로 우체국직원이 방문하여 접수하는 서비스</caption>
		<thead>
			<tr>
				<th colspan="2" scope="col">구분<br>(초과 ~ 이하)</th>
				<th scope="col">5kg 이하<br>(80㎝ 이하)</th>
				<th scope="col">5kg∼10kg<br>(80㎝∼100㎝))</th>
				<th scope="col">10kg∼20kg<br>(100㎝∼120㎝)</th>
				<th scope="col">20kg∼30kg<br>(120㎝∼160㎝)</th>
			</tr>
			</thead>
			<tbody>
			<tr>
				<th colspan="2" scope="row">익일배달</th>
				<td>5,000</td>
				<td>8,000</td>
				<td>10,000</td>
				<td>12,000</td>
			</tr>
			<tr>
				<th rowspan="2" scope="row">제주</th>
				<th scope="row">익일배달</th>
				<td>7,500</td>
				<td>10,500</td>
				<td>12,500</td>
				<td>14,500</td>
			</tr>
			<tr>
				<th scope="row">D+2 배달</th>
				<td>5,000</td>
				<td>8,000</td>
				<td>10,000</td>
				<td>12,000</td>
			</tr>
		</tbody>
	</table>

```
<h2>우체국택배(방문접수)</h2>
	<table class="price-table">
		<caption>고객이 원하는 장소로 우체국직원이 방문하여 접수하는 서비스</caption>
		<thead>
			<tr>
				<th colspan="2" scope="col">구분<br>(초과 ~ 이하)</th>
				<th scope="col">5kg 이하<br>(80㎝ 이하)</th>
				<th scope="col">5kg∼10kg<br>(80㎝∼100㎝))</th>
				<th scope="col">10kg∼20kg<br>(100㎝∼120㎝)</th>
				<th scope="col">20kg∼30kg<br>(120㎝∼160㎝)</th>
			</tr>
			</thead>
			<tbody>
			<tr>
				<th colspan="2" scope="row">익일배달</th>
				<td>5,000</td>
				<td>8,000</td>
				<td>10,000</td>
				<td>12,000</td>
			</tr>
			<tr>
				<th rowspan="2" scope="row">제주</th>
				<th scope="row">익일배달</th>
				<td>7,500</td>
				<td>10,500</td>
				<td>12,500</td>
				<td>14,500</td>
			</tr>
			<tr>
				<th scope="row">D+2 배달</th>
				<td>5,000</td>
				<td>8,000</td>
				<td>10,000</td>
				<td>12,000</td>
			</tr>
		</tbody>
	</table>
```

정리:

nvda 스크린리더기와 네레이터로 첫번째 코드와 두번째 코드를 비교해 보았다. 하지만 두 코드 모두 헤더와 값을 같이 읽어주었다. th와 td를 나누어 작성하면 기본적으로 헤더와 값을 연관지어 읽어준다. 하지만 th와 td를 나누었음에도 헤더와 값을 함께 읽어주지 않는 일부 보조기기에서 scope 속성의 진가가 나타날 듯 하다.

# 두번째 테이블(응용 + 심화)
## colgroup & rowgroup
첫번째 테이블과 달리 헤더의 구조가 조금 더 복잡합니다. 헤더의 카테고리가 상위 하위 카테고리로 나누어진 경우 그 관계를 나타내기 위해 colgroup 혹은 rowgroup을 사용할 수 있습니다.

### colgroup & rowgroup 사용법
scope에 colgroup과 rowgroup을 명시하기 전에, markup 구조를 먼저 만들어야 합니다.

- column을 묶고 싶은 경우 colgroup 태그를 caption 태그 아래에 작성한다.
- row를 묶고 싶은 경우 thead와 tbody, tfoot로 구조를 나눈다.

### 결과
<h2>소포우편(창구접수)</h2>
<table>
	<caption>1)등기소포</caption>
	<col>
	<col>
	<col>
	<colgroup span="2"></colgroup>
	<colgroup span="4"></colgroup>
	<thead>
		<tr>
			<th colspan="2" rowspan="2" scope="col">구 분<br>(초과 ~ 이하)</th>
			<th scope="col">80cm 이하</th>
			<th scope="col" colspan="2">80cm∼100cm</th>
			<th scope="col" colspan="4">100cm∼120cm</th>
			<th scope="col">120cm∼160cm</th>
		</tr>
		<tr>
			<th scope="col">3kg 이하</th>
			<th scope="col">3kg∼5kg</th>
			<th scope="col">5kg∼7kg</th>
			<th scope="col">7kg∼10kg</th>
			<th scope="col">10kg∼15kg</th>
			<th scope="col">15kg∼20kg</th>
			<th scope="col">20kg∼25kg</th>
			<th scope="col">25kg∼30kg</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th scope="row" colspan="2">익일배달</th>
			<td> 4,000 </td>
			<td> 4,500 </td>
			<td> 5,000 </td>
			<td> 6,000 </td>
			<td> 7,000 </td>
			<td> 8,000 </td>
			<td> 9,000 </td>
			<td> 11,000 </td>
		</tr>
		<tr>
			<th scope="rowgroup" rowspan="2">제주</th>
			<th scope="row">익일<br>배달</th>
			<td>6,500</td>
			<td>7,000</td>
			<td>7,500</td>
			<td>8,500</td>
			<td>9,500</td>
			<td>10,500</td>
			<td>11,500</td>
			<td>13,500</td>
		</tr>
		<tr>
			<th scope="row">D+2일<br>배달</th>
			<td>4,000</td>
			<td>4,500</td>
			<td>5,000</td>
			<td>6,000</td>
			<td>7,000</td>
			<td>8,000</td>
			<td>9,000</td>
			<td>11,000</td>
		</tr>
	</tbody>
</table>


```
<h2>소포우편(창구접수)</h2>
<table>
	<caption>1)등기소포</caption>
	<col>
	<col>
	<col>
	<colgroup span="2"></colgroup>
	<colgroup span="4"></colgroup>
	<thead>
		<tr>
			<th colspan="2" rowspan="2" scope="col">구 분<br>(초과 ~ 이하)</th>
			<th scope="col">80cm 이하</th>
			<th scope="col" colspan="2">80cm∼100cm</th>
			<th scope="col" colspan="4">100cm∼120cm</th>
			<th scope="col">120cm∼160cm</th>
		</tr>
		<tr>
			<th scope="col">3kg 이하</th>
			<th scope="col">3kg∼5kg</th>
			<th scope="col">5kg∼7kg</th>
			<th scope="col">7kg∼10kg</th>
			<th scope="col">10kg∼15kg</th>
			<th scope="col">15kg∼20kg</th>
			<th scope="col">20kg∼25kg</th>
			<th scope="col">25kg∼30kg</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th scope="row" colspan="2">익일배달</th>
			<td> 4,000 </td>
			<td> 4,500 </td>
			<td> 5,000 </td>
			<td> 6,000 </td>
			<td> 7,000 </td>
			<td> 8,000 </td>
			<td> 9,000 </td>
			<td> 11,000 </td>
		</tr>
		<tr>
			<th scope="rowgroup" rowspan="2">제주</th>
			<th scope="row">익일<br>배달</th>
			<td>6,500</td>
			<td>7,000</td>
			<td>7,500</td>
			<td>8,500</td>
			<td>9,500</td>
			<td>10,500</td>
			<td>11,500</td>
			<td>13,500</td>
		</tr>
		<tr>
			<th scope="row">D+2일<br>배달</th>
			<td>4,000</td>
			<td>4,500</td>
			<td>5,000</td>
			<td>6,000</td>
			<td>7,000</td>
			<td>8,000</td>
			<td>9,000</td>
			<td>11,000</td>
		</tr>
	</tbody>
</table>
```
정리: 

colgroup으로 헤더를 묶어주었을 때, 묶인 컬럼의 구조가 복잡하기 때문인지 처음에 한번만 헤더를 모두 읽어 준 후 셀 값을 모두 읽어줍니다. 테이블 행이 긴 경우 잘못사용하게 되면 스크린리더 사용자에게 혼동을 줄 수 있을 것 같아 행이 짧은 경우에 사용해야 할 것으로 보여집니다.

rowgroup의 경우는 왼쪽에서 오른쪽으로 읽어주는 흐름 대로 동일하게 읽어주어 어떤 차이가 있는지 확인하지 못했습니다.

## header & id
MDN에는 명시되어있지 않지만, 테이블 헤더 구조가 2줄 이상으로 나누어져있을 때 header와 id 속성을 사용해 셀이 어떤 헤더와 연관되어있는지 수기로 명시할 수 있습니다.


### Complicated tables
colspan과 rowspan을 사용해서 구조가 매우 복해진 테이블은 테이블 관계를 재정의해서 두 개의 테이블로 나누는 것도 하나의 방법입니다.


### 참조문서

- [w3](https://www.w3.org/WAI/tutorials/tables/)

- [seulbinim-blog](https://seulbinim.github.io/WSA/table.html#scope-id-headers-%EC%86%8D%EC%84%B1)

- [w3c-html-spec](https://html.spec.whatwg.org/multipage/canvas.html#examples)