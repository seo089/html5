# CSS 개요

> ## 1. CSS
CSS : Cascading Style Sheets
<br> 웹 문서 출력 시 디자인적인 부분을 지정하기 위해 웹 문서에 글꼴, 색상, 여백 등의 스타일을 기술하는 문서

> ## 2. CSS 적용 방법

#### 2-1. style 요소 사용 방법
`<head>` 요소 내에서 style 요소를 사용해서 스타일 정의
<br>각 HTML 페이지마다 동일한 요소에 통일성 있는 스타일을 적용하는 경우
```html
<head>
    <style>
        p {color: red; font-size: small}
    </style>
</head>
```

#### 2-2. style 속성 사용 방법
HTML 문서 각 요소에서 style 속성을 사용하여 스타일을 적용시키는 방법
<br>해당 요소에만 스타일이 적용되기 때문에 동일한 요소일지라도 다른 요소에 영향을 미치지 않음
```html
<p style="color: red; font-size: small;">CSS</p>
```

#### 2-3. 외부 파일 사용 방법
별도의 css 파일(.css)에 정의하여 `<head>` 요소 내 `<style>` 요소에 `@import`나  `link` 요소를 사용한다.
<br>프로젝트 전체에 통일감있는 스타일 적용이 가능하며, 유지보수에 용이하다.
<br>_W3C에서 권장하는 방법으로 대부분 웹사이트들이 이 방법을 주로 이용한다._

#### 2-4. CSS 적용 순서
style 속성을 사용한 방법 > style 요소를 사용한 방법 > 외부 파일을 사용한 방법 > 브라우저 디폴트 스타일
