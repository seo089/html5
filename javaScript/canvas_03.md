# Canvas Style

> ## 1. 선 스타일
1-1. 선 스타일 관련 속성

|속성|설명|
|:---:|---|
|context.strokeStyle|선의 색상 지정<br>값 : 색상명, 16진수 색상코드, rgb(), rgba(), 그라데이션, 패턴|
|context.lineWidth|선의 두께(기본값 1.0)를 픽셀 값으로 지정|
|context.lineJoin|두 선이 만나 꺾이는 모서리 부분의 모양을 지정<br>값 : bevel, round, miter(기본값)|
|context.lineCap|선의 양쪽 끝부분의 모양을 지정<br>값 : butt(기본값),round,square|

1-2. setLineDash() 메서드에서 점선 패턴 형식의 지정 예시

|메서드 예시|설명|
|:---:|---|
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
|:---:|---|
|context.shadowColor|그림자의 색상을 지정(기본값은 완전 투명한 검은색 rgba(0,0,0,0))|
|context.shadowOffsetX|대상을 기준으로 그림자의 수평(x좌표) 오프셋을 지정(기본값 0)|
|context.shadowOffsetY|대상을 기준으로 그림자의 수직(y좌표) 오프셋을 지정(기본값 0)|
|context.shadowBlur|그림자의 흐림 정도를 지정(기본값 0)|

### 4-2. 그림자 스타일 예제
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
context.fillStyle = 'rgba(255,0,0,1)';
context.shadowOffsetX = -5;
context.shadowOffsetY = -10;
context.shadowColor = 'black';
context.shadowBlur = 5;
context.fillRect(50,50,100,250);

context.shadowOffsetX = 10;
context.shadowOffsetY = 20;
context.shadowColor = 'black';
context.shadowBlur = 10;
context.fillRect(250,50,100,250);
</script>
```

> ## 5. 도형 합성

### 5-1. 도형 합성
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
context.beginPath();
context.fillStyle = 'green';
context.arc(75,100,60,0,2*Math.PI, true);
context.fill();
//먼저 그려진 도형을 대상 (destination) 이라 함
context.globalCompositeOperation = "속성값";
context.beginPath();
context.fillStyle = 'yellow';
context.arc(125,100,60,0,2*Math.PI,true);
context.fill();
//나중에 그려진 도형을 소스 (source) 라 함
</script>
```
### 5-2. globalCompositeOperation 의 속성 값
|속성값|설명|
|:---:|---|
|source-atop|대상 위에 소스 도형이 표시되지만 대상과 겹치지 않는 소스 부분은 표시 되지 않음|
|source-in|대상 안에 있는 소스 부분만 표시|
|source-out|대상 밖에 있는 소스 부분만 표시|
|source-over|기본값, 대상 위에 소스 도형을 표시|
|destination-atop|소스 위에 대상 도형이 표시되지만 소스와 겹치지 않는 대상 부분은 표시되지 않음|
|destination-in|소스 안에 있는 대상 부분만 표시|
|destination-out|소스 밖에 있는 대상 부분만 표시|
|destination-over|소스 위에 대상 도형을 표시|
|lighter|겹쳐진 부분은 두 색의 합을 구해서 표시|
|copy|대상은 무시, 소스만 표시|
|xor|대상과 소스의 겹쳐진 부분은 투명하게 표시|