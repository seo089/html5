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

### 2-2. 그라데이션 스타일

|메서드|설명|
|:---:|:---:|
|context.createLinearGradient(x1,y1,x2,y2)|선형 그라데이션 지정|
|context.createRadialGradient(x1,y1,r1,x2,y2,r2)|방사형 그라데이션 지정|
|context.addColorStop(오프셋, 색상)|그라데이션 경계색 지정|

### 2-3. 선형 그라데이션 예제
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
let gradient = context.createLinearGradient(0,0,150,150);
gradient.addColorStop(0,"red");
gradient.addColorStop(0.5,"yellow");
gradient.addColorStop(1,"green");
context.fillStyle = gradient;
context.fillRect(0,0,150,150);
</script>
```

### 2-4. 방사형 그라데이션 예제
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
let gradient = context.createRadialGradient(150,150,30,150,150,130);
gradient.addColorStop(0,"red");
gradient.addColorStop(0.5,"yellow");
gradient.addColorStop(1,"green");
context.fillStyle = gradient;
context.fillRect(0,0,canvas.width, canvas.height);
</script>
```

> ## 3. 패턴 스타일
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
let img = new Image();
img.src = "image.jpg";
img.onload = function() { // 이미지가 로드 완료되면 function 진행
    context.beginPath();
    let pattern = context.createPattern(img,"repeat");
    // 이미지 로드가 완료되면 메서드를 사용해서 이미지 패턴 객체를 생성
    context.fillStyle = pattern;
    // fillStyle 속성을 이미지 패턴 객체로 지정
    context.arc(100,100,70,0,2*Math.PI,false);
    context.fill();
    context.strokeStyle = pattern;
    context.lineWidth = 15;
    context.strokeRect(10,10,180,180);
}
</script>
```

> ## 4. 그림자 스타일 

### 4-1.그림자 스타일 관련 속성

|속성|설명|
|:---:|:---|
|context.shadowColor|그림자의 색상을 지정(기본값은 완전 투명한 검은색 rgba(0,0,0,0))|
|context.shadowOffsetX|대상을 기준으로 그림자의 수평(x좌표) 오프셋을 지정(기본값 0)|
|context.shadowOffsetY|대상을 기준으로 그림자의 수직(y좌표) 오프셋을 지정(기본값 0)|

