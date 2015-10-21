[float 해제하기] - 2015. 10. 21. 
 - 그래야 부모가 자식의 높이를 포함

1. 부모도 float시킴
 - 부모의 width가 float된 자식들의 width의 합 만큼이 됨. 브라우저 크기에 가변적으로 대응 불가.

2. 부모에게 overflow: auto 또는 overflow: hidden
 - 자식의 width의 합이 부모의 width를 넘는 경우 auto의 경우 스크롤이 생기고, hidden의 경우 잘리는 문제 발생

3. 빈 엘리먼트로 clear
 - 보통 빈 엘리먼트에 clear:both와 함께 height:0; overflow:hidden;등을 넣어 빈 엘리먼트가 보이지 않도록 하여 사용. 의미없는 빈 엘리먼트를 사용하는 문제가 있음.

4. 가상선택자 :after로 clear
- .parent{content:'', display: block; clear:both;}. 일반적으로 선호하는 방법.

5. 가상선택자 float해제 IE대응
- 문제: IE는 가상선택자를 지원하지 않음
- 해결: .parent{zoom:1;} //IE5~7대응
- 이유: IE5~7은 hasLayout성질을 갖게되면 float를 해제하는 트리거로 작용함.
		zoom:1;은 hasLayout성질을 갖게 함.

6. 부모의 display:inline-block속성 부텨
- 모든 브라우저에서 float을 해제할 수 있음
- 다만 표준계열 브라우저는 자식 width의 합이 부모의 width가 되지만, IE6~7에선 너비가 100%가 된다.
- inline-block이므로 여타 인라인요소와 마찬가지로 박스가 끝나는 지점에 4px정도의 공백을 갖게된다.

/* 
 *
 * 참조 사이트: http://naradesign.net/wp/2008/05/27/144/
 *
*/