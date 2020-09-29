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
