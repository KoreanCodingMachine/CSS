## CSS 문법

# CSS(Cascading Style Sheet) 개요
CSS는 HTML과 함께 웹을 구성하는 기본 프로그래밍 요소 입니다. HTML이 텍스트나 이미지, 표와 같은 구성 요소를 웹 문서에 넣어 뼈대를 만드는 것이라면 
CSS는 색상이나 크기, 이미지 크기나 위치, 배치 방법 등 웹 문서의 디자인 요소를 담당 합니다.

-CSS는 Cascading Style Sheet의 약어.
-CSS는 HTML로 부터 디자인적인 요소를 분리해 정의할 수 있음.
-잘 정의된 css 는 서로 다른 여러 웹페이지에 적용할 수 있음. -> 템플릿/테마
-자바스크립트와 연계해 동적인 콘텐츠 표현이나 디자인 적용 가능.

*CSS를 사용해야만 하는 이유
-웹 문서의 내용과 상관없이 디자인만 바꾸거나 디자인은 그대로 두고 웹 문서의 내용 변경이 용이.
-다양한 기기(PC, 스마트폰, 태블릿 등)에 맞게 탄력적으로 바뀌는 콘텐츠 -> 반응형 디자인(Responsive Design)
-동일한 문서구조를 가지고 서로 다른 CSS 테마 적용이 가능 함.

# CSS 기본 문법

CSS는 선택자와 선언부로 구성됩니다. 
선택자는 스타일을 지정할 HTML 요소(태그,아이디 등)를 가리킵니다. 선언부에는 CSS 속성 이름과 값이 포함됩니다. 속성이 여러 개일 경우,
한 줄로 나열해도 상관없지만 여러 줄에 걸쳐 작성하는 것이 좋습니다.

선택자  {속성:값; 속성:값....}

예)
/* h1태그의 색상을 빨간색으로 크기는 15px로 지정합니다.*/
h1 {color:red; font-size:15px;}
CSS 구문은 선택자(selector)와 선언부(declaration)로 구성.
선택자는 디자인을 적용하고자 하는 HTML요소. -> 선택자 정의가 중요
선언부는 콜론(:)으로 구분 되어진 다수의 항목을 포함.
각 선언은 항상 세미콜론(;)으로 끝나며, 선언블록은 중괄호({ })로 묶음.
/* comment */은 코드를 설명하는 데 사용됨.

선택자의 중요성
CSS의 핵심은 적절한 선택자를 사용하는 것이며 복잡한 문서 구조에서 특정 부분을 선택하기 위한 선택자 지정은 어려울 수 있으며 html 구조를 처음부터 잘 설계하는 것이 중요함.

# HTML 문서에 CSS를 적용하는 방법에는 내부 스타일시트, 외부 스타일시트, 인라인 스타일 등 총 3가지 방법이 있습니다.

1) 내부 스타일시트
html 파일에 스타일을 기술하는 방법으로 <head></head> 태그 사이에 <style></style> 태그 부분에 작성합니다.
html 과 css 가 한 파일에 있으므로 작업이 쉽고 간편하지만 css의 재활용이 안되는 문제가 있어 특별한 경우가 아니면 외부 스타일시트가 권장 됩니다.

<head>
<style>
body {
    background-color: red;
}

h1 {
    color: maroon;
    margin-left: 40px;
} 
</style>
</head>
<body>
    ...
</body>

2) 외부 스타일시트
css 를 작성하는 가장 기본적인 방법 입니다. 별도의 파일에 CSS 문서를 작성하고 해당 CSS를 필요로 하는 html 문서에서 불러와 사용하는 형식 입니다. 
이때 css는 동일한 서버에 있어도 되고 url을 통해 다른 서버의 css를 불러오는 것도 가능 합니다.

<link rel="stylesheet" type="text/css" href="mystyle.css">
<link rel="stylesheet" type="text/css" href="http://cdn.site.com/css/mystyle.css">

3) 인라인 스타일
html 태그에 필요한 디자인 속성을 직접 작성하는 형식 입니다. 그때 그때 필요한 디자인을 바로 적용할 수 있다는 편리함이 있지만 
일관된 디자인 체계를 유지하는 데에는 방해가 되기 때문에 꼭 필요한 경우가 아니라면 사용하지 않도록 합니다.

<h1 style="color:blue; margin-left:30px;">This is a heading</h1>

1) 캐스케이딩 의미
css 에서 Cascading 은 사전적 의미로 폭포처럼 떨어져 내리는 과 같은 의미를 가지고 있습니다. css 에서는 디자인 속성이 html 문서의 구조 
즉 DOM(Document Object Model) Tree 구조에서 상위 요소에서 정의한 디자인 속성이 하위 요소로 전달되는(상속 개념) 의미에서 유래 되었다고 할 수 있습니다.

상위 태그에서 정의된 디자인 속성은 하위 태그로 상속.
하위 태그에서 상위 태그에 정의된 디자인 속성을 변경할 수 있음.

<!-- body 태그 안에 있는 모든 태그 요소들은 빨간색 글자로 표시됨 -->
<body style="font-color:red">
    <h1>Hello</h1>
</body>

2) 우선 순위
동일한 디자인 속성이 외부 스타일시트, 내부 스타일시트, 인라인 스타일시트에 적용 되어 있는 경우 우선순위는 가장 나중에 정의되는 스타일에 있습니다. 
따라서 인라인 스타일시트가 가장 높은 우선순위로 적용되고 외부 스타일시트와 내부 스타일시트는 문서상 정의된 순서에 따라 우선순위가 결정되는 형식입니다.

웹 브라우저 자체도 html 구성요소에 대한 내부적인 css 를 가지고 있다고 볼 수 있습니다. 브라우저에 따라 사용자 정의 css를 사용할 수 있는것도 그 때문입니다. 
일반적인 우선순위(낮은순 -> 높은순)는 다음과 같습니다.

브라우저 디자인 정의 -> 외부 스타일시트 -> 내부 스타일시트 -> 인라인 스타일시트

## 셀렉터와 스타일 속성

스타일은 적용 대상이 있어야 하는데 셀렉터가 바로 그 대상입니다. 기본적으로 태그, 아이디, 클래스를 셀렉터로 사용하며 
이들을 조합해서 특정 조건에 맞는 셀렉터를 정의해 사용하게 됩니다.

html 문서에서 스타일의 적용 대상을 지칭.
디자인이 적용되기를 원하는 특정 부분의 선택이 용이하도록 적절한 태그 구조를 사용.
html 문서의 기본 구성요소인 태그는 가장 기본이 되는 셀렉터.
태그에 사용할 수 있는 id 속성은 문서내 유일한 값으로 셀렉터로 사용할 수 있음.
스타일 정의에 클래스를 사용하고 html 태그에 class 속성으로 스타일 지정.
셀렉터	사용예	사용예 설명
.class	 .intro	        html 태그에서 class=”intro”로 된 모든 태그 영역 선택
#id	      #banner     	html 태그에서 id=”banner”로  된 태그 영역 선택
*	                      *	문서내 모든 요소를 선택
태그	                  p	문서내 모든 <p> 태그 영역 선택
태그, 태그 div, p	      모든  <div> 와 <p> 태그 영역 선택
태그 태그 div p	        <div> 태그 안에 있는 모든 <p> 태그 영역 선택

1) 태그 셀렉터
태그 셀렉터는 태그 이름으로 요소를 선택.
문서내 임의이 태그를 선택자로 사용.
같은 디자인 속성을 가지는 여러 태그는 ,로 나열해 일괄적용.

p {
  text-align: center;
  color: red;
 }

h1,h2,h3,h4 { color: blue; }

경우에 따라서는 태그의 특정 속성에 대해 셀렉터를 지정하는 것이 가능 합니다. 예를 들면 <input> 태그는 type 속성에 따라 다양한 입력양식을 제공하게 되어 있습니다.
 이경우 특정 type 에만 배경색이나 크기를 지정하기 위해서는 다음과 같이 태그 셀렉터에 속성을 함께 사용합니다.

input[type=text] {
  background-color: blue;
  color: white;
}

2) id 셀렉터
HTML 요소의 id 속성을 사용해 특정 요소를 선택.
id는 페이지 내에서 유일한 값이기 때문에 하나의 고유한 요소를 선택하는 데 사용.

 #id_name { color: blue; }

---
<div id="id_name">
...
</div>

3) class 셀렉터

클래스 셀렉터는 특정 클래스 속성이 있는 요소를 선택.
.class name 형식으로 사용.
class로 디자인을 먼저 정해놓고 필요한 곳에서 해당 class를 지정해 사용하는 방식임.

.class_name1 { color: blue; }
p.class_name2 { color: red; }

---
<div class="class_name1">
...
</div>

03: 기본 셀렉터 조합
1) 동시 지정
,를 이용해 셀렉터를 나열하면 해당 셀렉터에 동일한 속성을 부여할 수 있습니다.

h1, h2 {...}
.box, .note {...}
  
2) 태그와 클래스 결합
태그와 클래스를 ,을 이용해 결합할 수 있습니다. 예를 들면 같은 클래스를 사용 하더라도 h1 과 h2 에 각각 다르게 적용하고 싶은 경우에 사용할 수 있습니다. 
다음 예제서는 .header 에 공통된 여러 속성을 적용해 두고 h1, h2에서는 각각 특정 속성만 변경하는 형식으로 많이 사용합니다.

.header { color: red; }
h1.header { color: blue;}
h2.header { color: green;}
header클래스를 사용하는 모든 태그의 텍스트는 붉은색으로 출력 됩니다.
h1에서 사용할 경우 파란색, h2의 경우 녹색이 적용 됩니다.
  
04: 속성 활용하기

1) 텍스트 속성
  
- color: 글자색 지정 
- text-align: 주어진 영역에서 글자의 정렬 방식 지정(left/right/center). 
- text-align: justify 의 경우 양쪽 정렬 
  
2) 폰트 속성

font-family
폰트의 이름과 유형을 지정하는 속성 입니다. 
영문을 기준으로 폰트의 유형은 세가지로 구분하며 다음과 같습니다.

Serif: 바탕체 계열의 폰트. Times New Roman, Georgia
Sans-serif: 굴림 계열의 폰트. Arial, Verdana
Monospace: 고정폭 폰트. Courier New, Lucida Console
 
font-family

폰트의 이름과 유형을 지정하는 속성 입니다. 영문을 기준으로 폰트의 유형은 세가지로 구분하며 다음과 같습니다.

Serif: 바탕체 계열의 폰트. Times New Roman, Georgia
Sans-serif: 굴림 계열의 폰트. Arial, Verdana
Monospace: 고정폭 폰트. Courier New, Lucida Console

h1 {
    font-family: "Times New Roman", verdana, arial;
}

폰트 이름이 두글자 이상인 경우 반드시 " "로 감싸야 함.
나열된 순서로 폰트가 적용됨.
마지막에는 fall back font 라고 해서 지정된 폰트가 없을 경우 사용할 폰트를 지정하는데 이름 보다는 폰트 유형을 지정하는 것이 좋다.
  
font-style
폰트의 스타일을 지정하는 속성 입니다. normal, italic, oblique 가 있으며 oblique 는 italic 과 유사하며 잘 사용되지 않습니다.

.text1 { font-style: normal}
.text2 { font-style: italic}
  
font-size
폰트의 크기를 지정하는 속성 입니다. px, %, rem, em 등 여러 단위로 사용할 수 있습니다. 

.text1 { font-size: 10px}
.text2 { font-size: 2em}
  
font-weight
폰트의 두께를 지정하는 속성 입니다. normal, bold, bolder 등을 사용할 수 있습니다.

.text1 { font-weight: normal}
.text2 { font-weight: bold}

font-variant
폰트의 변형을 지정하는 속성으로 normal, small-caps 를 사용할 수 있습니다. small-caps 는 소문자 크기를 유지하며 대문자로 변형해 주는 속성 입니다.
  
3) 정렬 속성
일반적인 문서 작성 프로그램에서는 텍스트나 이미지등을 가운데로 정렬하기가 쉽습니다. css 에서 가장 어려운 부분이 원하는 곳에 원하는 텍스트나 박스를 배치하는 것입니다.
기본적인 css 정렬 속성은 다음과 같습니다.

text-align: 요소내 텍스트의 정렬
vertical-align: 인라인 혹은 테이블 셀에서 수직 정렬


4) 링크 속성
하이퍼링크를 만들기 위한 <a> 태그에 적용할 수 있는 속성 입니다. html 의 기본 특성상 하이퍼링크 텍스트는 기본텍스트와 다른 색상을 가지고 마우스가 올라가면 색상이 변경되고 기본적으로 밑줄이 그어져 있습니다. 방문했던 사이트의 색상은 다르게 나와 디자인적인 일관성을 유지하려면 귀찮지만 관련된 속성을 모두 지정해 주어야 합니다. 다음은 <a> 태그에 적용되는 가상 셀렉터 입니다.

a:link - 방문한적 없는 기본 링크
a:visited - 방문한 링크
a:hover - 마우스가 링크위에 올라갔을 때
a:active - 링크를 클릭 했을 때
각각의 가상 셀렉터에는 color, background-color, text-decoration 등의 속성이 사용 됩니다.

a:link {
  color: red;
  text-decoration: none;
}

a:visited {
  color: blue;
  text-decoration: none;
}

a:hover {
  color: hotpink;
  text-decoration: underline;
}

a:active {
  background-color: blue;
  text-decoration: underline;
}
5) 컬러 속성
컴퓨터에서 사용하는 색상은 빛의 삼원색인 빨강색(Red), 초록색(Green), 파랑색(Blue)입니다. 이를 보통 RGB Color라고 부르는데, 각각의 색상은 0 ~ 255까지의 단계로 표현할 수 있습니다. 0부터 255를 16진수로 표현하면 00 ~ FF로 표현됩니다. CSS는 140개 이상의 색상이름, 16진수(HEX) 값, RGB 값 , RGBA 값, 불투명도를 지원합니다.
  
CSS에서 Color속성은 색상이름, HEX(#)코드, rgb, hsl로 나타낼 수 있습니다.
hsl 은 Hue(색조), Saturation(채도), Lightness(밝기) 의 조합을 나타냅니다.
색상에 투명도(alpha)를 적용시킬 때는 rgba, hsla를 사용하며, 0.0(완전투명)~1.0(완전불투명) 사이의 숫자로 나타냅니다.
  
CSS Color
  
#text1 { color: red; }
#text2 { color: #FF0000; }
#text3 { color: rgb(255, 0, 0); }

rgba, hsla

#text1 { color: rgba(255, 99, 71, 0.5) }
#text2 { color: hsla(9,100%, 64%, 0.5) }
  
7) 배경 속성
색상이나 이미지를 배경으로 지정하기 위한 속성 입니다. 대표적인 속성들은 다음과 같습니다.

background-color: 글자색 지정
background-image: 배경이미지 지정, 상대경로, 절대경로, url 사용가능
background-repeat: 이미지 반복
background-position: 이미지의 위치를 지정
background-attachment: 이미지의 스크롤이나 고정을 지정함

body {
  background-image: url("back_img.png");
  background-repeat: no-repeat;
  background-position: right top;
  background-attachment: fixed;
}


