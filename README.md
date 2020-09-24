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



Browser
-------------

브라우저에서 웹페이지를 열게 되면 Window라는 전체적인 오브젝트가 존재한다. Window는 페이지뿐만 아니라 브라우저안에 현재 열려있는 전체 창을 의미한다. 그리고 Window안 페이지가 표시되는 부분이 Document 오브젝트이다. Document는 우리가 HTML에서 작성한 요소들이 표기되어지는 부분이다. 사용자의 눈에는 보이지 않지만 전체적으로 Window에 관련된 브라우저 자체에 관련된 정보들이 담겨있는 Navigator라는 오브젝트도 있다.

브라우저를 열게 되면 Window라는 전체적인 오브젝트가 있고 그 Window안에 DOM(Document Object Model)이 들어있다. 이제 이 DOM을 이용해서 새로운 요소를 추가하고 빼고 움직이는등을 가능하게 한다. 그리고 BOM(Browswer Object Model)이라는 것도 있다. BOM은 브라우저에 관련된 아이들 Navigator나 Location이나 Fatch 그리고 Web APIs에 관련된 오브젝트들이 들어 있다.

브라우저에서 가장 위에있는 오브젝트는 Window로 콘솔창에 this라고 출력하면 Window가 나온다.



브라우저 좌표
-------------
Client x,y 와 Page x,y
Client x,y 는 사용자가 보는 페이지에 상관없이 브라우저 윈도우 창에서 x,y가 얼마나 떨어져 있는지가 전달이 된다.
Page x,y 는 클라이언트에 들어있는 사이즈가 아니라 문서의 처음 시작에서 떨어져 있는 x와y를 의미한다.
 
 
 
Window load
-------------
### load
```
    <script>
       window.addEventListener('load', () => {
            console.log('load');
        });
    </script>
```
load는 리소스, 즉 페이지 안에서 쓰이고 있는 폰트나 이미지 css 같은 것들이 다 다운되면 호출이 된다
브라우저가 html파일을 열게 되면 처음 부터 html페이지를 읽어서 DOM 요소로 변환한 다음 스크립트 부분을 만나면 윈도우에 이벤트 리스너를 등록하게되고 윈도우에서 페이지에 필요한 모든 리소스가 다 로딩이 완료가 되면 콜백함수를 실행한다.



### DOMContentLoaded
```
<script>
	window.addEventListener("DOMContentLoaded", () => {
	console.log('DOMContentLoaded');
        });
</script>
```
DOMContentLoaded는 html만 다 완료가 되면 이것이 호출 된다. 자바스크립트 파일이 이미지나 폰트 를 사용하지 않으면 DOMContentLoaded안에서 동작을 수행하는 것이 조금 더 빠르게 사용자가 화면을 볼 수 있는 장점이 있다.
defer옵션이나 DOMContetnLoaded라는 이벤트는 html만 완료가 되면 호출 되기 때문에 리소스가 많은 경우에는 DOMContetnLoaded으로 빠르게 화면을 보여주고 load는 조금 후에 리소스가 다 준비되면 보여 줄 수 있다



### beforeunload 와 unloaded

```
<script>
	//로드가 안될 때, 즉 페이지가 끝날 때 호출 되는 beforeunload
        //브라우저에서 사용자가 나갈때, 그 직전에 불러지는 함수 
	window.addEventListener('beforeunload', () => {
            console.log('beforeunload');
        });

        //리소스가 모두다 unloaded 되었을 때
        window.addEventListener('unloaded', () => {
            console.log('unloaded');
        });
</script>
```
브라우저에서 사용자가 페이지를 나갈 때 호출 되는 것들이다
beforeunload는 unloaded 되기 전에 호출이 되고
unloaded는 리소스들이 모두 unloaded가 되었을 때 호출이 된다.
그래서 사용자가 페이지를 나가지 전에 뭔가 해야한다면 여기에 콜백함수를 등록해서 처리 할 수 있다




Async vs defer
---------------
 
html에서 javascript를 포함할 때 어떻게 포함하는게  효율적인지 알아본다.

### head에 스크립트 파일을 넣는 경우
```
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
        <script src="main.js"></script>
    </head>
    <body></body>
</html>
```

브라우저가 HTML 파일을 한줄씩 분석한다(parsing)
 
한 줄씩 분석을 하다가 스크립트 태그를 만나면 스크립트를 다운받아야 한다고 이해하게 된다.
그래서 HTML을 parsing하는 것을 잠시 멈추고 필요한 자바스크립트 파일을 서버에서 다운받아서 그것을 실행한 후 다시 HTML을 parsing하게 된다.

* 단점은?
사용자가 웹사이트 전체를 보게 되는 데 까지 시간이 많이 걸린다. 그래서 스크립트를 헤드에 그냥 포함하는 것은 좋은것이 아니다. 

![제목_없는_아트워크 2](https://user-images.githubusercontent.com/50136014/94115044-2817ad80-fe84-11ea-8276-4406b92a7696.jpg)



### body 마지막에 스크립트를 넣는 경우
```
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
        
    </head>
    <body>

        <script src="main.js"></script>
    </body>
</html>
```
이렇게 하게 되면 브라우저가 HTML전체를 parsing하고 준비가 된다음에 스크립트를 다운받게 되어 실행하게 된다. 그럼 사용자는 먼저 페이지를 볼 수 있다는 장점이있다.

* 단점은?
만약 웹사이트가 자바스크립트에 많이 의존적이라면 즉, 사용자가 의미있는 컨탠츠를 보기 위해서는 HTML을 받는 시간뿐아니라  자바스크립트도 받고 실행하는 시간까지 걸리기 때문에 사용사는 많이 기다리게 될 수 도 있다.

![제목_없는_아트워크 3](https://user-images.githubusercontent.com/50136014/94115183-54cbc500-fe84-11ea-80b2-ad7c5435f735.jpg)


### head안에 스크립트 && asyc라는 속성을 넣는 경우 
```
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
        <script asyc src="main.js"></script>
    </head>
    <body>
    </body>
</html>
```
asyc는 boolean타입의 속성값이다. 그래서 선언하는 것 만으로도 true가 된다.
asyc로 설정하게 되면 브라우저가 html을 parsing하다가 asyc가 선언된 스크립트를 만나게 되면 그 스크립트를 병렬로 다운받자고 명령만 해놓고 다시 html을 parsing하다가 main.js가 다운이 완료 되면 html parsing을 멈추고 maing.js를 실행한다. 실행이 완료 되면 나머지 html을 parsing을 한다. 이렇게 하면 장점은 body끝에 사용하는 것 보다는 병렬로 다운받고 parsing햐기 때문에 시간을 절약할 수 있다.
하지만 자바스크립트가 html이 다 다운 되기 전에 실행이 되기 때문에  자바스크립트에서 필요한 Html요소가 아직 다운이 다 되지 않은 경우가 생길 수 있다.
또 자바스크립트를 다운하고 실행하는 동안 html 다운은 언제든지 멈출수 있기 때문에 사용작 페이지를 보는데 시간이 많이 걸릴수 있다 

![제목_없는_아트워크 4](https://user-images.githubusercontent.com/50136014/94115199-58f7e280-fe84-11ea-82a0-d0baad2ef5c7.jpg)

### head안에 스크립트를 && defer이라는 속성을 넣는 경우
```
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <title>Document</title>
        <script defer src="main.js"></script>
    </head>
    <body>
    </body>
</html>
```
이 경우에는 html parsing하다가 스크립트를 만나면 다운로드를 받자고 명령만 시켜 놓고 나머지 html을 parsing 하게 된다. 그리고 마지막에 parsing이 끝난 후에 다운받아 놓은  자바스크립트를 실행한다

![제목_없는_아트워크 5](https://user-images.githubusercontent.com/50136014/94115200-5a290f80-fe84-11ea-9541-8dbe4219b8b6.jpg)

’use strict’; 정의하는 이유
-------
자바스크립트는 유연하게 만들어졌다. 유연하다는 것은 굉장히 위험할 수 있다는 뜻이 될 수 있다.  Use strict를 선언하면 비상식적인 부분이 제한 된다. 


DOM(Document Object Model)
---------------

DOM은 브라우저에서 html 파일을 열면 브라우저가 html파일을 읽어서 모든 태그들을 분석해서 노드로 변환하는데 브라우저가 이해할 수 있는 오브젝트로 변환한 것이다. 

### Node

html 파일에서 쓰인 태그가 자바스크립트에서는  Node 라는 오브젝트로 변환이 된다. 그리고 이 노드의 오브젝트 안에는 우리가 작성한 클래스나 텍스트등의 정보가 포함 되어있다.
또 이 노드라는 오브젝트는 EventTarget이라는 오브젝트를 상속한다. 따라서  Node라는 오브젝트는 EventTarget의 오브젝트라고 할 수 있어 모든 Node는 이벤트가 발생할 수 있다. 
document는 Node를 상속하기 때문에 또 EventTarget도 상속을 한다. 그래서 document에서 이벤트가 발생 할 수 있다. html요소들은 Element로 변환이 되기 때문에 모든 html요소에서 이벤트가 발생 할 수 있다. 
element에도 종류가 많이 있는데 html 요소라면 HTMLElement라고 한다.  HTMLElement 안에는 어떤 태그를 쓰냐에 따라 HTMLInpuElement HTMlDivElement HTMlLmageElement등 많은 태그별로 Elelment 가 존재한다.

### DOM Tree

브라우저가 html 파일을 읽으면서 DOM 트리로 변환하여 브라우저가 이해 할 수 있는 것으로 만드는 것이다. Html 에 있는 각각의 태그들이 DOM요소와 하니씩 대응할 수 있다. 

### EventTarget

Node는 모두 EventTarget을 상속하기 때문에 EventTarget에서 지원하는 API를 사용 할 수 있다.
addEventListener()
removeEventListener()
dispatchEventListener()



CSSOM(CSS Object Model)
-----------------------

브라우저에서 DOM을 만들게 되면 CSS를 병합해서 CSSOM이라는 것을 만든다. 모든 스타일(html파일 안에 들어있는 스타일이나 css파일에 정의 한 css 또는 브라우저가 기본적으로 가지고 있는 스타일)에 관련된 정보들은 합하고 DOM과 CSS요소를 병합해서 CSS DOM이라는 트리리틑 다시 만든다. CSSOM에는 우리가 정의한 스타일뿐만아니라 브라우저에 기본 설정 값 cascading룰에 따라 합해진 css의 모든 값이 정의 되어 있다. 

그래서 브라우저가 html파일을 읽기 시작하면 제일 처음 DOM트리를 만들고 다음 css파일을 읽고 최종적인 css스타일 트리를 만든다. 그후 DOM과 CSSOM을 합쳐서 최종적으로 브라우저에 표기될 것만 Render트리에 표기가 된다. 
예를 들어 opacity:0 이나 visibility:hidden은 Render트리에 포함이 되지만 display:none은 Render트리에 포함 되어 있지 않는다. 



랜더링 순서
--------

브라우저에 URL을 입력하게 되면 다음과 같은 순서를 거친 후에 화면에 보여진다. 
 
Requests/response->loading-> scripting->rendering->layout->painting->composition
⌊_________________construction__________________⌋ ⌊__________operation_________⌋

html파일을 서버에서 받아 로딩을 하고 html을 읽어 DOM요소로 변환하는 scripting을 진행하고 CSS요소를 CSSOM으로 변환한다. 그후에 브라우저 윈도우에 표기를 하기 위해서 준비를 하는데 Rendering 트리를 만든 후에 어디에 얼만한 크기로 표기 할지 계산을 한후 painting을 진행한다.

위의 진행사항을 두가지로 나눈다면 html을 브라우저가 이해할 수 있는 DOM으로 바꾸고 최종적으로 RenderTree를 만드는  construction부분과 Rendering 트리를 보고 배치하고 브라우저 윈도우에 그림을 그리는 operation 부분으로 나눌 수 있다. 

**layout**과정은 renderTree의 정보를 기반으로 윈도우 위에 어느위치에 어느정도의 크기로 놓을지 구상하는 단계이다. 

그 후 **paint**단계를 거치는데 layout단계 후 바로 윈도우에 그리는 것이 아니라 요소들이 어떻게 배치되어 있는지를 기준으로 각 부분을 쪼개어서 이미지를 레이어가 쌓여 있는 것처럼 해놓는다. 이렇게 해 놓으면 투명도를 변환하거나 아이템의 위치가 바뀌가나 할 때 전체적으로 그림을 지우고 다시 그리는 것이 아니라 수정 해야할 부분만 다시 그리면 되기 때문에 전체를 지우고 다시 그리는 것보다 성능이 좋아진다.
성능개선을 위해서 CSS에 will-change라는 속성값을 주게 되면 변경될지 모르니 새로운 레이어에 그 아아템을 놓는 준비를 해둘 수 있다. 

**composition**단계는 준비된 레이어를 순서대로 브라우저 위에 표기한다. 

이렇게 html페이지에서 브라우저를 표기하는 단계들을 **critical rendering path**라고 한다. 

#### construction부분에서 rendering트리를 만들 때 어떻게 하면 빠르게 만들 수 있을까?
DOM요소가 작을 수록 CSS양이 작을 수로 트리가 빠르게 만들어 진다. 따라서 불필요한 태그를 쓰는 것을 좋지 않다.
또 operation부분에서는 처음 표기 후에 나중에 사용자가 클릭을 하는등 움직임이 있을 때 paint가 자주 일어나지 않게 만드는 것이 중요하다. 
예를 들어 페이지에 한 네모 아이템이 있는데 그 아이템을 tranclate을 이용해서 움직이면 어떤 과정이 발행할까? translate를 이용하게 되면 paint는 일어나지 않고 레이어의 위치만 움직이면 된다. 즉 composition 만 수행하면 되기 때문에 성능이 좋게 작동 할 수 있다. 하지만 성능이 최악인 경우에는 아이템의 포지션을 바꾸어 layout부터 변경하여 paint composition까지 모두 바꾸는 것이다. 

#### css속성값 알기
http://csstriggers.com/


