Let's study Web
=============

Web APIs(Application Programming Interfaces)
-------------

APIs란?
예를 들어 자판기에서 음료를 뽑을 때 자판기가 어떻게 작동하는지 몰라도 동전을 넣고 버튼하나만 누르면 원하는 기능을 수행 할 수 있다. 

마찬가지로 windows에서 제공하는 APIs를 사용하면 간단하게 윈도우 어플리케이션을 만들 수 있고 안드로이드나 맥OS에서 제공하는 APIs를 사용하면 간단하게 모바일 어플리케이션을 만들 수 있다. 또는 유튜브에서 제공하는 API를 사용헤서 유튜브에 있는 데이터를 받아 올 수도 있다.이렇게 OS나 플랫품에서 제공하는 API도 있지만 진행하는 프로젝트에서 UserStorage라는 클래스에 로그인과 로그아웃에 대한 함수가 있따면 UserStorage클래스에서 제공하는 두가지 APIs가 있다고 할 수 있다.

이처럼 Web APIs는 브라우저에서 제공하는 것이다. 브라우저마다 공통적으로 제공하는 API 많이 있는데 DOM APIs, Network APIs, 그래픽 관련 APIs등 여러가지가 있다. 

HTTP와 HTTPS
-------------
Web APIs 중에서 HTTPs에서만 동작할 수 있다는 경고가 있는 것들이 있다.

브라우저는 사용자의 정보를 보호할 의무가 있기 때문에 정보보안에 굉장히 민감하다.  HTTP(Hypertext transfer Protocol)는 웹 클라이언트와 서브가 어떻게 통신하는지 통신규약을 정해 놓은 것으로 클라이언트가 서버에게 정보를 요청하고 다시 서버에서 정보를 받아오는 request를 하고 response를 방아온느 방식으로 이루어져 있다.
HTTPS는 HTTP에 S가 더해진 아이이다. Hypertext transfer Protocol Secure의 약자이다. 즉 정보를 주고 받는 것들이 잘 감싸져있는 보안 처리가 되고 있다는 말이다. 
