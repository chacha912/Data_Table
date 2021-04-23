# 접근성을 고려한 table 마크업
## 스크린 리더를 사용하여 table의 정보를 들을 때, 필요한 것
1. 어떤 table이 있을 때, 그게 현재 찾고자 하는 table인지 아닌지, table 안의 내용을 들을 지 판단할 수 있어야 한다.
   + 이를 위해, **&lt;caption&gt; - table의 제목**이 필요하다.
2. table 안 셀의 내용이 어떤 것을 의미하는 건지 알 수 있어야 한다.
    + **&lt;th&gt;** 와 **&lt;td&gt;** 로 제목 셀과 내용 셀을 구분해야 한다.
    + 단순한 table의 경우, **scope** 로 table을 읽는 방향을 설정해주어야 한다.
    + 복잡한 table의 경우 **id** 와 **header** 로 제목 셀과 내용 셀의 관계를 분명하게 해주어야 한다.
3. 점수 통계 및 등수와 같은 table 종합 정보를 모든 셀을 확인하기 전 알 수 있도록 한다.
    + &lt;thead&gt;, &lt;tfoot&gt;, &lt;tbody&gt; 순으로 마크업한다. (그래도 t&lt;tfoot&gt; 요소는 table의 가장 마지막에 렌더링된다.)

---

### **&lt;caption&gt;** - table의 제목
스크린 리더를 사용할 때, 현재 페이지의 table 목록에서 table의 제목이 있으면 그 제목을 읽어준다. 그러면 그 table의 내용을 모두 들어보기 전에 어떤 내용에 대한 table인지 알 수 있다.
만약 table의 제목이 없다면, table 목록에서 읽어주는 정보는 그 table이 몇행 몇열인지 밖에 없다.
페이지에 table이 둘 이상 있다면  각 table이 무엇인지 알 수 있도록 &lt;caption&gt;을 추가하는 것이 바람직하다.
> table의 제목을 넣는다고 제목 요소(h1, h2 등)을 사용하지 않도록 주의해야한다. 이런 제목 요소는 table과 결합된 요소가 아니기 때문에 table의 목록에서 table의 제목으로 인식하고 제공하지 못한다.

> &lt;catpion&gt; 요소는 &lt;table&gt;요소 바로 다음에 와야한다.

---

### **&lt;th&gt;** 와 **&lt;td&gt;**
사람이 눈으로 table을 읽을 땐, 어떤 게 내용 셀이고 어떤 게 제목 셀인지, 둘 사이가 어떤 관계를 맺고 있는 지를 알 수 있다.
하지만 스크린 리더를 사용할 때, 내용 셀과 제목 셀을 마크업에서 구분해두지 않는다면 모든 것을 동일하게 읽어주기 때문에 table의 각 셀이 어떤 의미를 가지는 지 파악할 수 없다.
그러므로 &lt;th&gt;를 이용하여 table 헤더를 만들어 내용 셀과 제목 셀을 구분해주어야 한다.

---

### **scope** 로 table을 읽는 방향을 설정해주어야 한다.
&lt;th&gt;를 이용하여 table 헤더를 만들었다면, 그 제목 셀과 데이터 셀을 연결해주어야 한다.
scope 속성을 사용할 경우, 각 제목 셀이 행의 제목 셀인지 열의 제목 셀인지를 선언함으로써 제목 셀과 내용 셀을 연결한다.

스크린 리더 사용시, 이 scope를 기준으로 읽는 방향을 고려하기 때문에
단순한 table의 경우, **scope** 로 table을 읽는 방향을 설정해주어야 한다.

scope="col"을 선언하면, 해당 셀이 열의 맨 위에 위치함을 설명한다. scope="row"를 선언하면, 해당 셀이 행의 맨 앞에 위치함을 설명한다.
scope="rowgroup"을 선언하면, 그룹으로 묶인 여러 개의 행 그룹의 헤더임을 설명한다.
scope="colgroup"을 선언하면, 그룹으로 묶인 여러 개의 열 그룹의 헤더임을 설명한다. 

![da](./img/data_table1.png)

---

### **id** 와 **header** 로 제목 셀과 내용 셀의 관계를 분명하게 해주어야 한다.
제목 셀과 관련이 없는 데이터 셀이 섞여있거나 thead에 셀 제목이 2개 이상 인 경우, 병합이 많이 된 경우 등과 같은 복잡한 table에서는, **id** 와 **header** 로 제목 셀과 내용 셀의 관계를 분명하게 해주어야 한다.
각 &lt;th&gt;에 고유한 id 속성 값을 주고, 각 &lt;td&gt; 셀에 headers속성에 &lt;th&gt;의 id 속성값을 할당한다. 하나의 데이터 셀은 여러 개의 headers값을 가지며 여러 개의 제목 셀과 관계를 이어줄 수 있는데 각 값은 공백으로 구분한다.

> 가장 좋은 건 table을 최대한 단순하게 만들어 scope만으로 충분하도록 하는 것이다. 

> scope와 동시에 쓰는 것은 권장되지 않는다. 

### table 종합 정보를 모든 셀을 확인하기 전 알 수 있도록 한다.
스크린 리더를 사용할 때, 점수 통계 및 등수와 같은 table 종합 정보를 모든 셀을 확인하기 전 알 수 있도록 &lt;thead&gt;, &lt;tfoot&gt;, &lt;tbody&gt; 순으로 마크업한다. 그래도 t&lt;tfoot&gt; 요소는 table의 가장 마지막에 렌더링된다.

***

## 저시력자 확대 고려
저시력자의 경우, table을 확대해서 보는 일이 많다. 
셀의 너비를 정의할 때 고정된 픽셀값으로 지정한다면, 확대 시 가로 스크롤이 길어지게 된다.
가로 스크롤 사용은 가독성에 영향을 주기 때문에 백분율과 같은 상대적인 값을 사용하여 가로 스크롤을 최소화하면서도 크게 볼 수 있도록 지원해주어야한다.

이는 &lt;colgroup&gt;을 이용할 수 있다.

> &lt;colgroup&gt;은 &lt;caption&gt;의 뒤에 와야하며, &lt;thread&gt; &lt;th&gt; &lt;tbody&gt; &lt;tfoot&gt; &lt;tr&gt; 요소의 위에 있어야한다.

***

## 가장 중요한 건 table을 원래 용도로 사용해야한다는 것이다.
테이블을 레이아웃 용도로 사용하거나, 표의 구분을 위한 의미없는 빈 셀 사용,, 데이터 셀 안에 구분선 사용 등은 지양해야 한다.

***

## 참고 문서
+ [표의 내용을 이해하기 쉽게 제공하기](https://brunch.co.kr/@snclab/31)
+ [scope,id,headers 속성](https://seulbinim.github.io/WSA/table.html#thead-tbody-tfoot-%EC%9A%94%EC%86%8C)
+ [접근성 테이블(scope,id & headers)](https://webclub.tistory.com/264)
+ [웹 접근성 자습서](https://www.w3.org/WAI/tutorials/tables/)
+ [table 요소 MDN 문서](https://developer.mozilla.org/ko/docs/Web/HTML/Element/table)
+ [caption 요소 MDN 문서](https://developer.mozilla.org/ko/docs/Web/HTML/Element/caption)
+ [table scope rowgroup, colgroup](https://worker-k.tistory.com/entry/table-%ED%83%9C%EA%B7%B8-%EC%9B%B9-%EC%A0%91%EA%B7%BC%EC%84%B1-caption-scope-%EC%A4%91%EC%8B%AC%EC%9C%BC%EB%A1%9C)
+ [ARIA:rowgroup role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/Rowgroup_Role)
+ [colgruop element MDN 문서](https://developer.mozilla.org/ko/docs/Web/HTML/Element/colgroup)