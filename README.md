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
