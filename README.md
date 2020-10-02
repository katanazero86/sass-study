# sass-study
- created : 2020-09-30
- 목적 : sass 에 대해서 좀 더 친숙해지고 익숙해지기 위한 학습
- 참고 : 웹디자이너를 위한 SASS(http://www.yes24.com/Product/Goods/14121531)

## 왜 SASS 인가?
- SASS 는 CSS 전처리기(CSS preprocessor) 이며, 전처리기 언어로 작성된 코드를 일반 CSS 코드로 변환해준다.😀(컴파일러 역할을 해준다고 생각하면 편하다.)
- CSS 에서 색상을 바꿔야 한다고 했을 때 그 값을 일일이 찾아서 바꾼다면 매우 비효율적이다. 여기서 SASS 를 사용한다면 아래와 같이 유지보수가 가능하다.
```
$text-color: #868686;

a {
  color : $text-color;
}

p {
  color : $text-color;
}

```
- CSS 에서 반복되는 스타일 블록들은 어떨까?
```
p {
  margin-bottom : 20px;
  font-weight : 600;
}

h1 {
  margin-bottom : 20px;
  font-weight : 600;
}

// SASS
@mixin default-text-style {
  margin-bottom : 20px;
  font-weight : 600;
}

p {
  @include default-text-style;
}

h1 {
  @include default-text-style
}
```
> 🤩Wow! 반복되는 스타일들을 정의해서 공통적으로 재사용하는게 보이는가? 이제는 CSS 파일 하나하나찾아가면서 작업을 하지 않아도 된다!
> 위 2가지 예제는 SASS 가 CSS 를 얼마나 쉽고 빠르고 융통성 있게 작성해주는지 살펴 볼 수 있다.

---

## CSS 는 어렵다.
- CSS 는 어렵다. 속성, 적용순위, 브라우저마다 상이한 지원속성, 선택자, 쿼크모드(Quirks mode) 등 이 모든것 완벽하게 이해하기란 쉽지 않다.
- 지나치게 반복적이다.
- CSS 는 모두 전역범위로 적용되고 속성이 상속이 되며(물론 상속이 안되는 속성도 존재한다.), 제일 힘든 문제는 오류가 생기기 쉽다.
- CSS 의 공동 창시자 버트 보스(Bert Bos) 의 글을 보면 왜 CSS 가 수년간 문법의 한계를 갖고 있을 수 밖에 없었는지 이해할 수 있다.
> CSS 는 프로그래머들이 매크로, 변수, 기호 상수, 조건문, 표현식과 같은 프로그래밍 언어에서 사용하는 효과적인 기능을 받아들이지 않고 멈추어 있다. 그런 기능이 제공된다면 고급 전문가는 자신이 원하는대로 작성할 수 있지만 경험이 부족한 초보자는 자신도 모르게 포기할 것이다. 아니, 아예 겁을 먹고 시작도 하지 않을 것이다. 일종의 균형잡기인 셈이다. CSS 에서의 균형은 다른 언어와 다르다.

> 🤔 CSS 의 초기 설계자들은 이런 기능의 도입을 걱정했으며, 그들은 가능한 한 많은 사람이 웹사이트를 만들기를 원했습니다. CSS 가 웹 페이지에 스타일을 적용하면서 내용과 표현을 분리할 수 있을 정도로 강력하며, 동시에 쉽게 이해되고 사용되기를 바랬습니다.

---

## DRY 원칙
- Don't Repeat Yourself : DRY -> 반복되는 코드를 만들지 말라
- 중복되어 작성된 코드가 개발자 또는 협업을 하는 사람에게 혼란을 주지말아야 한다.(혼란을 주면 작업이 느려지고, 실패할 확률이 늘어난다.)
- 공통적으로 반복되는 패턴을 작성하여, 이것을 재사용해야한다. 이런 방식은 효율적이고 유지보수하기가 쉽다.
- CSS 에는 DRY 를 적용할 수 없다. 동일한 코드를 CSS 코드내에서 많이 보았을거다. (CSS 는 변수, 상수, 조건문, 표현식 등과 같은 프로그래밍 언어에서 사용하는 기능이 없음)

---

## SASS 란 무엇인가?
- SASS 는 CSS 전처리기
- SASS(Syntactically Awesome Stylesheets) 는 하나의 언어로서 CSS 의 구멍을 메워주고 DRY 방식을 적용하여 더 빠르고 효율적으로 코드를 작성하고 쉽게 유지보수할 수 있게 해준다.
- SASS 는 CSS 상위에 있는 메타언어(meta-language) == 고차언어
- 보통 CSS 에서는 변수 또는 믹스인 등의 좋은 기능들을 사용할 수 없지만 SASS 에서는 가능

## SASS 문법
- SASS 에는 서로 다른 두 개의 문법이 있다. SCSS 가 최신문법이며, SCSS 파일은 .scss 라는 파일 확장자를 사용한다. SASS 파일은 .sass 라는 파일 확장자를 사용한다.
- SCSS 작성방식은 우리가 잘 알고 있는 CSS 작성방식과 비슷하며, SASS 는 중괄호화 세미콜론이 빠진문법이라 낯설수도 있다.
```
//scss
$pink: #ea4c89;

p {
  font-size: 12px;
  color: $pink;
}

//sass
// 중괄호와 세미콜론이 사라지고 공백과 들여쓰기로 선언의 구조를 알려준다.
$pink: #ea4c89
p
  font-size: 12px
  color: $pink
```

---

## 윈도우에서 SASS 설치하기
- Mac OS X 와 달리 윈도우에는 루비가 설치되어 있지 않다. SASS 공식 웹 사이트에서 윈도우용 루비인스톨러(Ruby-Installer) 설치를 권장한다. (현재 루비 SASS 는 2019.03.26일자로 지원이 중단 되었다. -> 자세한 내용은 https://sass-lang.com/ 참조)

## SASS 에게 감시할 watch 파일 알려주기
- SASS 에게 어떤 파일을 감시하라고 알려주면, 우리가 스타일시트를 편집하는 동안 SASS 는 해당 파일을 모니터닝한다. 우리가 코드를 변경할 때마다 SASS 는 SASS 문법이 잘 작성되어 있는 .scss 파일을 웹 브라우저에서 해석될 준비가 된 .css 파일로 변환해준다.
> sass --watch test.scss:test.css
> 위 명령어를 실행하면 SASS 는 test.scss 파일에 변화가 있는지 감시하며, 해당 파일에 변화가 감지되면 test.css 로 변환하고 기존 내용을 변경된 내용으로 최신화 시킨다.(덮어버린다)
- SASS 에게 디렉터리를 통째로 감시하라고도 명령어를 작성할 수 있다.
> sass --watch <input folder>:<output folder>
> sass --watch scss:css
> 위 명령어를 실행하면 SASS 는 scss 폴더 전체를 감시하며, 폴더내에서 파일에 변화가 감지되면 .css 로 변환한 결과물을 css 폴더에 반영한다.
  
## 명령어 대신 애플리케이션 사용하기
- 명령어를 사용하기도 하지만, 애플리케이션을 사용하여 SASS 파일을 쉽게 모니터링하고 출력 파일을 관리할 수 있다.
- 스카우트(https://scout-app.io/)
- 라이브리로드(http://livereload.com/)

---

## SASS 사용하기

- SASS test 사이트 : https://www.sassmeister.com/
1. 중첩규칙(nesting)
> SASS 를 이용하면 선택자를 다른 선언문에서 계속 반복해서 쓰지 않고 선언문 안에 중첩해서 작성이 가능하다. 중첩하는 것도 마크업의 구조를 그대로 반영한다.
```
.logo {
  display : flex;
  
  img {
    width : 100%;
  }
}

// compile CSS
.logo {
  display : flex;
}

.logo img {
  width : 100%;
}
```
> SASS 는 선택자에서 각 요소를 반복하지 않고 계층 구조를 나타내는 중첩방식으로 코드를 간단하게 만든다. 선택자를 정황하게 늘여놓은 필요가 없다.

2. 네임스페이스 속성 중첩
> 중첩 규직을 추가하는 것과 마찬가지로 SASS 에서는 공통된 네임 스페이스 속성도 중첩이 가능하다.
```
.header {
  font : {
    size : 54px;
    weight : bold;
  }
}

.body {
  background : {
    color : black;
    position : top left;
    size : 16px 16px;
    image : url();
    // ...
  }
}
```
> 이와 비슷하게 ```text- / background-``` 네임 스페이스 속성도 있다. 

3. & 로 부모 선택자 참조하기
> SASS 는 특수기호 **&** 로 부모선택자를 참조할 수 있다.
```
a {
  color : red;
  
  &:hover {
    color : blue;
  }
}

// CSS

a {
  color : red;
}

a:hover {
  color : blue;
}
```
> & 선택자가 위 코드에서는 a 태그 선택자를 가리킨다.
> 아래는 다른예시다. 스타일을 덮어쓰기할 때 유용하다.
```
li a {
  color : blue;
  
  &.success {
    color : green
  }
}

.list {
  
  font-weight : normal;

  &__bold {
    font-weight : bold
  }
}
```

4. SASS 에서 주석 달기
```
/* 이것은 최종 .css 파일에서 보일
여러줄 짜리 주석이다. */

/*! 이것은 최종 .css 파일에서 보일
여러줄 짜리 주석이다. 심지어 압축된 스타일에서도 말이다. */

// 이것은 한줄 짜리 주석이다.
// 한줄 짜리 주석들은 .css 에서 삭제된다.
```

5. 변수
> **$** 를 사용하여 변수를 정의할 수 있다. 변수는 유지보수 작업을 훨씬 간편하고 쉽게 만들어준다.
```
$color : #333;
$fontSans : Arial, sans-serif;

body {
  color : $color;
  font-family : $fontSans;
}
```
> SASS 변수를 사용함으로써 CSS 문서에서 반복되는 값을 일일이 고치는 엄청난 작업을 단 몇 초 안에 해결할 수 있게 되었다.

6. darken / lighten 컬러 기능을 이용하여 다른 음영 컬러 만들기
> **darken / lighten** 기능을 이용하여 다른 음영 컬러를 만들 수 있다.
```
$primaryColor : #007bff;
$primaryColorDark30 : darken($primaryColor, 30%);
$primaryColorLight30 : lighten($primaryColor, 30%);

.test {
  color : $primaryColorDark30;
  font-weight : bold;
  font-size : 20px;
}

.test2 {
  color : $primaryColorLight30;
  font-weight : bold;
  font-size : 20px;
}

<div class='test'>
    123456
</div>

<div class='test2'>
    123456
</div>
```

7. 믹스인(mixin)
> 믹스인은 스타일 블록을 정의하고 재사용하게 해준다. 여러 가지 선언에서 똑같은 규칙을 사용하여 단 한 번만 스타일 그룹을 정의하고 필요할 때마다 그것을 참조 할 수 있다. **@mixin** 지시자를 이용하여 정의한다. 인자를 전달도 가능하며, 기본값도 정의가 가능하다.
```
@mixin scroll {
  overflow : auto;
}

@mixin titleStyle {
  margin : 0 0 20px 0;
  font-size : 20px;
  font-weight : bold;
}

@mixin colorStyle($color : #eee) {
  color : $color
}

@mixin borderRounded($radius : 4px) {
  -webkit-border-radius : $radius;
  -moz-border-radius : $radius;
  border-radius : $radius;
}

.title h2 {
  @include titleStyle;
  @include scroll;
  @include color(#868686);
  @include borderRounded(8px);
}
```
> 믹스인을 라이브리러리 형식으로 작성하여 사용도 가능하다.
```
// mixins.scss
@mixin colorStyle($color : #eee) {
  color : $color
}

@mixin borderRounded($radius : 4px) {
  -webkit-border-radius : $radius;
  -moz-border-radius : $radius;
  border-radius : $radius;
}

// page.scss
@import './mixins.scss';
```
> @import 명령어로 mxins.scss 를 불러와서, @include 구문으로 호출해서 사용이 가능하다.
> SASS 에서 컴파일할 때, @import 명령어로 불러온 SCSS 파일들은 CSS 파일 하나로 합쳐진다.(HTTP 요청 횟수를 줄이며, 웹 사이트 성능에 유리하다.)

8. 상속(extend)
> 공통 스타일을 정의하여 상속시킬 수 있다. 중복을 최소화해주고 공통 스타일을 정의할 수 있으니 편리하다. **@extend** 지시자를 사용한다.
```
.box{
	padding:20px;
	border:1px solid #333;
}
 
.news-box{
	@extend .box;
	background-color:#eee;
}
 
.list-box{
	@extend .box;
	background-color:#000;	
}

// CSS
.box, .news-box, .list-box { padding: 20px; border: 1px solid #333; }
.news-box { background-color: #eee; }
.list-box { background-color: #000; }
```
> ```<div class="box news-box"></div>``` 이런 형식으로 추가 클래스를 만드는 작업을 최소화 시킬 수 있다.
> @extend 로 플레이스홀더 선택자를 사용하면, 오로지 다른 스타일을 확장하려는 목적으로만 사용도 가능하다. **%** 를 클래스 이름 앞에 붙여 플레이스홀더를 표시해준다.
```
%button {
  padding : 10px;
  font-weight : bold;
}

.submit {
  @extend %button;
  background-color : green;
}
```

---

## SASS 와 미디어 쿼리(Media queries)
- 반응형 프로젝트에서 SASS 를 어떻게 사용하는지 살펴보자.

1. 미디어 쿼리 구문
```
<link rel="stylesheet" media="screen and (max-width: 768px)" href="mystyle.css" />

@media screen and (max-width: 768px) { 
  body { 
    background-color: lightgreen; 
  } 
}

@media (min-width: 1024px) {
  // CSS
}

@media (min-width: 375px) and (max-width: 1024px) {
  // CSS
}

@media all and (min-width:1024px) {
  // CSS
}

max-width : 최대 너비를 설정합니다. 브라우저의 너비가 max-width 값 이하인 경우에만 CSS가 적용
min-width : 최소 너비를 설정합니다. 브라우저의 너비가 min-width 값 이상일 경우에만 CSS가 적용

미디어 유형 (생략시 default 값은 all)
all 모든장치
screen 컴퓨터 화면 또는 스마트 기기 화면
tv 영상과 음성이 함께 출력되는 장치
projection 프로젝터 장치
handler 손에 들고다니는 소형장치
speech 음성 출력 장치
aural 음성 합성 장치 (화면을 소리로 출력해주는 장치)
embossed 점자 인쇄 장치 (화면을 읽어 종이에 점자를 찍어내는 장치)
tty 디스플레이 기능이 제한된 장치
braille 점자 표시 장치
width 웹페이지 가로 너비
height 웹페이지 세로 높이
device-width 기기의 가로 너비
device-height 기기의 세로 높이
orientation 기기의 화면방향 (portrait:세로,landscape:가로)
aspect-ratio 화면 비율
device-aspect-ratio 단말기기의 화면 비율
color 기기의 비트 수
color-index 기기의 색상 수
monochrome 기기가 흑백일 때 픽셀당 비트 수
resoulution 기기의 해상력
scan TV의 스캔 방식
grid 기기의 그리드/비트맵

```

2. 미디어 쿼리 중첩하기
> SASS 에서는 원래의 선언 안에 미디어 쿼리를 중첩할 수 있습니다.
```
section.main {
  width : 50%;
  font-size : 16px;
  
  @media (max-width: 700px) {
    width : 100%;
    font-size : 12px;
  }
}

// CSS
section.main {
  width : 50%;
  font-size : 16px;
}

@media (max-width: 700px) {
  section.main {
    width : 100%;
    font-size : 12px;
  }
}
```
> 중단점(break point)을 SASS 변수로 정의해서 사용한다. 미디어 쿼리를 사용할 때마다 해당 변수값을 참조하게 할 수 있다. 중단점값을 한곳에서 관리하니 매우 편리하다.
```
$mobile : 375px;
$desktop : 1023px;

section.main {
  width : 50%;
  font-size : 16px;
  
  @media (max-width: $mobile) {
    width : 100%;
    font-size : 12px;
  }
  
  @media (min-width: $desktop + 1) {
   // 심지어 연산도 가능하다!!
   // CSS
  }
  
}
```

3. @content 블록과 믹스인 결합시키기
- SASS 의 **@content** 지시자를 사용하여 스타일 블록 전체를 믹스인으로 넘길 수 있다.
```
@mixin responsive($range) {
	@if $range == desktop {
		@media (min-width: $desktop) { @content; }
	} @else if $range == mobild {
		@media (max-width: $mobile) { @content; }
	}
}

.cards { 
  padding : 10px;
  &-index {
		margin-top: 16px;
	}
	&-item {
		padding: 16px;
	}
  
  @include responsive(mobile) {
		padding: 4px;
		&-index {
			margin-top: 8px;
		}
		&-item {
			padding: 0 16px;
		}
	}
  
}
```
> **@content**  지시어는 미디어쿼리에 삽입할 믹스인에 스타일 블록이 넘어오는거다. 반복되는 코드가 줄고 반응형 디자인 작업이 간단해진다.

4. 반응형에 따라 flex column 구현하기(12 columns grid)
- SASS 를 이용하면, bootstrap / vuetify 에서 이용하는 flex 12 columns grid layout system 을 쉽게 구현 가능하다.
- Interpolation: **#{}** -> 인터폴레이션은 변수의 값을 문자열 그대로 삽입

```
@function get-size($column) {
	@if $column == 1 { @return (100% / 12); }
	@else if $column == 2 { @return (100% / 12) * 2; }
	@else if $column == 3 { @return (100% / 12) * 3; }
	@else if $column == 4 { @return (100% / 12) * 4; }
	@else if $column == 5 { @return (100% / 12) * 5; }
	@else if $column == 6 { @return (100% / 12) * 6; }
	@else if $column == 7 { @return (100% / 12) * 7; }
	@else if $column == 8 { @return (100% / 12) * 8; }
	@else if $column == 9 { @return (100% / 12) * 9; }
	@else if $column == 10 { @return (100% / 12) * 10; }
	@else if $column == 11 { @return (100% / 12) * 11; }
	@else if $column == 12 { @return (100% / 12) * 12; }
}

@mixin render-col($type) {
  @for $i from 1 to 13 {
    .col#{$type}-#{$i} {
      flex-grow : 0;
      flex-shrink : 0;
      flex-basis : get-size($i);
      max-width: get-size($i);
    }
  }
}

@include responsive(desktop) {
  @include render-columns('-lg'); // desktop
}

@include responsive(mobile) {
  @include render-columns('-xs'); // mobile
}

.d-flex-row {
  display : flex;
  flex-direction : row; 
}

.row {
  @extend .d-flex-row;
  flex-wrap : nowrap
}

.row-wrap {
  @extend .d-flex-row;
  flex-wrap : wrap;
}

.align-items {
  &-start {
    align-items: flex-start;
  }

  &-center {
    align-items: center;
  }
  //...
}

.col {
   flex-basis: 0;
   flex-grow: 1;
   flex-shrink : 1;
   max-width: 100%;
}
```
> 위와 같이 사용하면, flex 속성을 활용하여 12 column grid layout 을 쉽게 클래스들을 생성하여 사용이 가능하다.(.col-xs-1 / .col-lg-12)<br/>
> 반응형을 담당하는 믹스인을 호출하여 내부에서 다른 믹스인을 호출한다.(중첩 믹스인) 믹스인에 클래스명에 생성될 column 문자열을 전달한 후, **@for** 문을 활용하여 생성해준다. 
