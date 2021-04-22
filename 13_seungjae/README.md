#안승재 table#

1.  테이블의 웹접근성 고려사항(caption, id, headers)  
    -> table에 caption요소를 통해 사용자에게 표콘텐츠를 확인할지, 넘어갈지 결정하게 도움을 줄 수 있음  
    -> colspan, rowspan이 있는 table은 복잡한 표에 속한다고 합니다. 복잡한 표는 스크린 리더와 같은 보조 기술의 분석을 어렵게 한다고 합니다. 그래서 될 수 있으면 표를 여러개 나눠서 colspan, rowspan을 쓰지 않는게 좋다고 합니다. 하지만 표를 나눌 수 없을 땐 id, headers특성을 이용합니다. 그래서 우체국 테이블에선 복잡한표에 id와 headers 속성을 주었습니다.  
    [https://developer.mozilla.org/ko/docs/Web/HTML/Element/table#%EC%A0%91%EA%B7%BC%EC%84%B1_%EA%B3%A0%EB%A0%A4%EC%82%AC%ED%95%AD]
2.  <br>태그를 그냥 써도 괜찮은가?  
    -> 아래 블로그를 참고하여 br태그 같은 단일 태그도 닫는 기호 /> 를 달아주는게 확실히 명시가 되기 때문에 웹접근성을 향상시킨다는 것을 알게됨  
    [https://penguingoon.tistory.com/162 ]
