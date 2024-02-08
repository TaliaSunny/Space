# Space
우주 사이트 구성!

idea
1. 우주와 나와의 거리 관련해서 수식 넣어두고 랜덤성으로 위치 선정 후 
그에 따른 내 위치와 우주 천체 사이의 거리를 측정해주는 거.
이를 타로 혹은 별자리 등의 이야기를 넣어주면서 웹 혹은 사이트 구현을 해준다.
타로 같은 기능인거지 -> posteller 같은 기능을 해주는데 

2. 만약 기준점을 바꾸고 싶다면 무작위로 위치 선정 
그리고 이걸 단어를 스크립트릿으로 좋은거 갯수가 많은거  나쁜거 많은거 선택해ㅓㅅ
이를 정렬 후에 좋은 것과 나쁜것을 보여준다.

또한 물리 하는 학생들을 위한 

현재 거리와 수식 설명에 대한 app을 만들어도 좋긴할듯
솔직히.. 쉬운데.. 

상대성이론에 대해서 대하여 특수는 일단 초기에 prototype에 사용하고
일반 상대성이론에 대한 이론적 기술과 그거에 대한 설명 내용을 간략히 
해주는 사이트 참고 문헌 사이트도 좋겠다.

물리학을 배웠으니까 그걸 이용하는 방향으로 전개해도 나쁘지 않고

수리 물리 영역과 같은 경우 
- 공대 / 수학/ 과학과  3영역으로 다 방면에 쓰이는데
현재 시행하는 math lap 어쩌구 사이트는 3회~ 정도만 무료인걸로 알고 있고 
설명도 한국어보다 영어권 아이들이 많이 사용하는것을 알고 있지.

그렇다면 이 부분에 사진을 찍으면 텍스트 구현 혹은 너무 알아보기 어렵다면 사진 그 자체로 하고 
올릴때 어떠한 수식 도구를 선택하면 자동적으로 수식을 구현해주고 입력하는 방식으로 구현하고
값도 구해준다면 편하겠네?

이 부분은 아마 수식계산기 영역을 참고하면 될것이다.

하지만 현재 수식 계산기의 한계점은 
입력이 힘든점과
범위가 넘어가면 오류가 뜬다는점

그런 부분에 대해서 바꿔주고 
수식적인 부분은 c++을 이용해서 다루게 하고 (계산이 빨라야 하기 때문에)
이를 그래프와 하고 이미지화 해주는 부분은 ?
javascript 기반으로 해줘도 좋겠네.

그리고 chatbot처럼 일정 수준으로 물어보면 그에 따른 참고도서나 링크를 알려주는 사이트
이를 mashine learning 영역인데 이 부분에 대해서 공부해보면 좋겠다.



admin 계정의 경우 기존의 방식 jsp파일이 맞다 

하지만 member 계정의 경우 기존의 방식이 아닌
접속한 member id = 그 해당 member id의 내용들만 뿌려 주어야 한다. 



total.jsp에서 로그인한 사용자의 mid와 연결된 내용만 화면에 보여주려면 다음과 같은 방법을 사용할 수 있습니다:

먼저, 로그인한 사용자의 mid를 어딘가에서 가져와야 합니다. 이것은 세션, 쿠키, 또는 다른 방법을 통해 수행할 수 있습니다. 이 예제에서는 세션을 사용합니다.

사용자가 로그인한 후에 mid가 세션에 설정된다고 가정하면, 다음과 같이 mid를 가져옵니다:

jsp
Copy code
<%
    String mid = (String) session.getAttribute("mid"); // 세션에서 mid 가져오기
    if (mid == null || mid.isEmpty()) {
        // mid가 없거나 비어 있으면 어떤 작업을 수행할 수 있음 (예: 로그인 페이지로 리디렉션)
        response.sendRedirect("login.jsp"); // 로그인 페이지로 이동
    }
%>
위의 코드는 세션에서 mid를 가져와서, 만약 mid가 없거나 비어 있으면 로그인 페이지로 리디렉션합니다.

mid가 있는 경우, mid를 사용하여 데이터베이스에서 해당 사용자와 연관된 내용을 가져옵니다. 이것은 mid를 사용하여 SQL 쿼리를 작성하고 데이터베이스에서 데이터를 검색하는 것을 의미합니다.

가져온 데이터를 total.jsp에서 출력하면 됩니다. 예를 들어, mid와 연결된 동물 프로필 목록을 출력하는 방법은 다음과 같습니다:

jsp
Copy code
<%
    // mid로 데이터베이스에서 해당 사용자와 연관된 동물 프로필을 가져온다.
    AnimalProfileDAO dao = new AnimalProfileDAO();
    List<AnimalProfileVO> animalProfiles = dao.getProfilesByMid(mid);
%>

<!-- 동물 프로필 목록을 출력 -->
<table>
    <tr>
        <th>동물 번호</th>
        <th>이름</th>
        <th>품종</th>
        <th>나이</th>
        <th>성별</th>
    </tr>
    <c:forEach var="animal" items="${animalProfiles}">
        <tr>
            <td>${animal.ano}</td>
            <td>${animal.aname}</td>
            <td>${animal.atype}</td>
            <td>${animal.aage}</td>
            <td>${animal.agender}</td>
        </tr>
    </c:forEach>
</table>
위의 코드는 AnimalProfileDAO에서 mid를 사용하여 동물 프로필 목록을 가져와서 total.jsp에서 출력하는 방법을 보여줍니다.

이 코드는 사용자가 로그인하고 세션에서 mid를 설정한 경우에만 동작합니다. 로그인하지 않은 사용자를 처리하기 위한 추가 로직이 필요할 수 있습니다.


 요 방식에 대해서 이제 사용하면 된다.


방사청 무기체계 소프트 웨어 개발 및 관리 매뉴얼
모아소프트 . 슈어 소프트. 한컴 mds  신뢰성 시험 툴을 팔거나 의뢰 받음

// SW 신뢰성 시험 정적/ 동적 시험
정적 시험 : 프로그램 돌리지 X = > 스페이스 간격 똑같은걸 해도 룰을 지켜서 해야 함.

동적 시험 : 모든 코드가 메뉴얼대로 모든 코드가 타고 다 에러가 없어야 됨.

소프트웨어 보안약점 진단가이드
정적 시험은 통과해야지 정부 관려된거는 납품 가능하다.

정부 정보화 소프트 웨어 산출물 
 관련 제안서 라든가 양식 참고해서 우리꺼 새로 업데이트 시키자.



여기서 사진 정보라든가 그런거 있는데 그 부분을 
이용해서 특정 위치당 경로 지정해서 머신 러닝 데이터 돌리는건데
그정도로 하기는 어렵고 . 
그냥 이미 만들어진 애들이 open소스라서 
그거 이용하려고요

ARINC 424
 - 국제 항공 표준 !

브이월드 - V-World
https://map.vworld.kr/map/ws3dmap.do?mode=MAPW201



### mungdaum

멍다움 사이트 

사용한 방식 
- (DDD) 대충 설명 하고
- 사용한 방식의 단점과 장점 이를 보완하기 위해서 어떠한 노력을 했는지 issue를 통해서 확인하도록 링크걸기
- ppt 이미지 같은거 넣어주기
- 
view 테이블 - DDD 
테이블 :
storyassistant(전개자에 대한 방식....)
???
근데 우리는 이런 방식 사용을 안했는데?
생활코딩
| member | product |notice|cart|order|event|qna|
|------|------|------|------|------|------|------|
|      |       |||||

문제점과 issue해결 방안

자바 인터페이스를 활용한 도메인 주도 설계(DDD)
xml mapper는 interface였네..
- interface는 자바에서 클래스와 클래스 사이에 중개자 역할
- interface는 다중구현이 가능하다.

- 나는 https://twofootdog.github.io/Spring-DAO%EC%99%80-Mapper%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90/
- 
- Controller.java - Service.java - Mapper.java - Mapper.xml구조 [더 최근의 것]
- Controller.java - Service.java - DAO.java - Mapper.xml구조


근데 내 구조는? 그냥 service.java - 
[](https://jung-story.tistory.com/128)https://jung-story.tistory.com/128

Class 사용
장점
쿼리문 실행 전에 넣어줄 매개변수와 쿼리 결과값의 변형을 정의할 수 있다.
Namespace를 내 마음대로 둘 수 있다.
.xml 파일의 쿼리문 id와 mapper 메소드명을 일치시킬 필요가 없다.
단점
Sqlsession 객체를 주입받아야 하며, 쿼리문 실행 시 항상 호출해야 한다.
쿼리문 호출 시 sqlsession에 .xml 파일의 namespce와 쿼리문 id를 매개변수로 넘겨야한다.

Interface 사용
장점
메소드의 내부 구현이 불필요하다.
Sqlsession 객체 주입이 불펼요하다.
.xml 파일의 쿼리문 id와 mapper 메소드 명이 일치한다.
단점
.xml의 Namespace가 실제 Mapper.java 위치를 가르켜야 한다.
메소드 내부 정의가 불가능하다.

interface로 사용했다.
