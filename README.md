[ OnPaint ]<br>
화면 출력을 위한 함수<br>
그 밖에 윈도우에서 사용<br>
View 에서 Overriding 가능 단, Overriding 시 OnDraw 출력 안됨<br>

[ OnDraw ]<br>
화면 출력 뿐만 아니라 프린터 출력에도 관여하는 함수<br>
View 클래스에서 사용<br>

[ CClientDC ]<br>
Window영역의 캡션바 메뉴바 상태바 등을 제외한 클라이언트 영역만을 관리하는 DC를 뜻한다.<br>
WM_PAINT메시지가 발생하지 않았을 때 화면에 그림을 그리기 위해 사용한다.<br>
내부적으로 GetDC(), ReleaseDC()함수를 사용해서 구현되어있다.<br>

[ CPaintDC ]<br>
WM_PAINT 메시지가 발생했을때 다시 그려져야 할 영역에 대한 DC를 관리한다.<br>
WM_PAINT 메시지 핸들러인 OnPaint()함수에서 사용한다.<br>
BeginPaint()함수와 EndPaint()함수로 이루어진다.<br>
MFC 뷰클래스를 WM_PAINT 메시지를 받으면 내부적으로 CPaintDC클래스를 생성하고, OnDraw()함수를 호출해준다.<br>
그래서 OnDraw()함수를 WM_PAINT처럼 처리하는 것이다.<br>

**CPaintDC 와 CClientDC 는 유사한 것같은데 동일하게 사용하면 되는가?**
 
생성된 윈도우가 다른 윈도우에 가려져서 무효화영역(Invalid Region)이 발생하게 되면 WM_PAINT메세지가 호출되고 WM_PAINT메세지를 처리하는 메세지 핸들러에서 무효화 영역이 복구되어진다.<br>
다이얼로그 기반대화상자에서 WM_PAINT메세지는 OnPaint() 라는 메세지 함수에서 처리하게 된다.<br>

[ 도큐먼트(Document) ] <br>
데이터를 관리는 기능을 구현한 클래스데이터를 저장하거나 읽어 들인다.<br>
데이터의 변경 사항이 생기면 뷰의 화면을 갱신한다.<br>

[ 뷰(View) ] <br>
데이터를 화면에 표시하는 기능을 구현한 클래스데이타를 화면에 표시한다.<br>
사용자와 상호 작용을 담당한다.<br>
