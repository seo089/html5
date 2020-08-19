# Canvas Style

> ## 1. 선 스타일
1-1. 선 스타일 관련 속성

|속성|설명|
|:---:|:---|
|context.strokeStyle|선의 색상 지정<br>값 : 색상명, 16진수 색상코드, rgb(), rgba(), 그라데이션, 패턴|
|context.lineWidth|선의 두께(기본값 1.0)를 픽셀 값으로 지정|
|context.lineJoin|두 선이 만나 꺾이는 모서리 부분의 모양을 지정<br>값 : bevel, round, miter(기본값)|
|context.lineCap|선의 양쪽 끝부분의 모양을 지정<br>값 : butt(기본값),round,square|

1-2. setLineDash() 메서드에서 점선 패턴 형식의 지정 예시

|메서드 예시|설명|
|:---:|:---|
|context.setLineDash([2])|선의 길이 2픽셀, 공백의 길이 2픽셀 <br> ==--==--==--... 패턴|
|context.setLineDash([2,3])|선의 길이 2픽셀, 공백의 길이 3픽셀 <br> ==---==---==---... 패턴|
|context.setLineDash([5,4,3,2])|두 가지 패턴의 반복<br>선의 길이 5픽셀, 공백의 길이 4픽셀, 다시 선 3픽셀, 공백 2픽셀 <br> =====----===--=====----===--... 패턴|

1-3. 점선으로 그리기
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
context.beginPath();
context.lineWidth = 10;
context.setLineDash([2]);
context.rect(100,100,100,100);
context.stroke();
</script>
```

> ## 2. 채우기 스타일
### 2-1. fillStyle 속성과 globalAlpha 속성
- fillStyle : 도형을 채우는 색상을 지정
- globalAlpha : 색상의 투명도를 지정, 값 : 0.0(완전 투명) ~ 1.0(완전 불투명)

