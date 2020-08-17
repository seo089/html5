# Canvas

## canvas 란?
자바스크립트 코드를 이용해서 웹브라우저에 그림을 그리는 기능
<br>기존 HTML에서는 `img` 요소를 사용하거나 자바 애플릿, 플래시 같은 별도의 플러그인을 사용하였으나
<br>HTML5의 `canvas` 를 사용하면 별도의 프로그램 설치 없이 그림 표현이 가능하다.
<br>그림의 합성, 변환, 애니메이션 같은 효과도 표현 가능
<br>*모바일 단말기나 PC등 HTML5를 지원하는 모든 브라우저에서 작동*

### canvas의 좌표 시스템
2차원 그래픽 제공을 위해 2차원 좌표 시스템 사용 
<br>왼쪽 모서리가 (0,0) 기준점

### canvas와 context 객체
- canvas 요소
<br> 캔버스 영역은 웹페이제엇 그림이 그려지는 사각형 영역으로 `canvas`요소를 사용한다.
```html
<canvas id="캔버스 객체 아이디" width="폭" height="높이">
    <!--defalut 는 width 300px height 150px 이다.-->
    <!--캔버스 영역 자체는 웹 브라우저 화면에 아무것도 표시 되지 않기 때문에 css를 지정해서 영역을 확인해 볼 수 있다.-->
</canvas>
```

- canvas와 canvas context 찾기
<br>`var canvas = document.getElementById("canvas 요소의 id");`
<br>`canvas`는 단지 컨텍스트를 위한 컨테이너 같은 역할만을 담당하고, 실제 그림 그리는 기능은 모두 컨텍스트를 통해 처리 된다.
<br>`var context = document.getElementById("canvas 요소의 id").getContext("2d");`

- canvas 작업의 기본 형태
<br> `body` 요소 내 영역을 지정하고 `script` 내 자바스크립트 코드로 실제 그림을 그린다.

