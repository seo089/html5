# Canvas 그리기

## 선과 도형 그리기

> ### 1. 사각형 그리기

1-1. 사각형 그리기 관련 메서드

|메서드|설명|
|:---:|---|
|context.strokeRect(x,y,w,h)|테두리만 있는 사각형을 그린다.|
|context.fillRect(x,y,w,h)|색이 채워진 사각형을 그린다.|
|context.clearRect(x,y,w,h)|지정한 사각형 영역을 지운다.<br>실제로는 영역 안의 모든 픽셀을 투명한 검은색으로 채운다.)|

1-2. 사각형 그리기 예제 코드
```html
<canvas id="myCanvas"></canvas>

<script>
let context = document.getElementById("myCanvas").getContext("2d");
canvas.width = 300;
canvas.height = 300;
canvas.style.backgroundColor = "lightyellow";
context.lineWidth = 10;
context.strokeStyle = "blue";
context.fillStyle = "green";
context.strokeRect(50,50,100,100);
context.fillRect(150,150,100,100);
context.clearRect(100,100,100,100);
</script>
```

> ### 2. 선 그리기
```
1. beginPath() 메서드 -> 패스를 초기화 한다.
2. 다양한 메서드 -> 패스를 지정하고 선이나 도형을 그린다.
3. closePath() 메서드 -> 지정한 패스를 닫는다.
4. stroke() 또는 fill() 메서드 -> 선이나 도형을 출력한다.
```

2-1. **패스 기반 메서드**

|메서드|설명|
|---|---|
|context.beginPath()|이전의 패스를 모두 지우고 새로운 패스를 그린다.|
|context.closePath()|현재 패스를 닫는다.<br>둘 이상의 점을 가진 경우에는 마지막 점과 첫번째 점을 연결하는 직선을 추가하여 닫힌 모양의 도형을 만든다.|
|context.moveTo(x,y)|주어진 점을 시작으로 새로운 서브패스를 만든다.|
|context.lineTo(x,y)|바로 이전의 점과 현재의 점을 연결하는 선을 그린다.|
|context.rect(x,y,w,h)|사각형을 그린다.|
|context.arc(...)|원/원호를 그린다.|
|context.stroke()|현재 패스에 있는 도형들을 선 스타일로 실제로 캔버스에 그린다.|
|context.fill()|현재 패스에 있는 도형들을 채우기 스타일로 실제로 캔버스에 그린다.|

2-2. 선 그리기 예제 코드
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
context.beginPath();
context.moveTo(50,50);
context.lineTo(200,200);
context.stroke();
</script>
```

> ### 3. 다각형 그리기
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
context.beginPath();
context.moveTo(100,25);
context.lineTo(175,177);
context.lineTo(25,175);
context.closePath();
context.stroke();
/*stroke()가 아니고 fill() 메서드를 사용한다면 내부가 색(기본 검정색)으로 채워진 도형 출력*/
</script>
```

> ### 4. 원 그리기
4-1. 원 그리기 예제
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
context.beginPath();
context.arc(100,100,75,0,2*Math.PI,true);
context.stroke();
/* 6개의 인자
원/원호의 중심 좌표 x,y, 반지름, 시작각도, 종료각도, 그리는 방향
그리는 방향 >>
true : 반시계방향, false : 시계방향
*/
</script>
```

4-2. 직선과 접하는 원호 그리기
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
context.moveTo(30,30);
context.arcTo(100,170,180,80,50);
/*arcTo 메서드로 보조점(x1,y1), 종료점(x2,y2) 점을 찍고 접점에 원호를 그린다.*/
context.stroke();
context.fill();/*원호 내부 채우기*/
</script>
```

> ### 5. 베지에 곡선 그리기
베지에 곡선(Bezier Curve)은 n개의 점으로부터 얻어지는 n-1차 곡선을 의미한다.
- 2차 베지에 곡선 quadraticCurveTo()
<br> 2차 베지에 곡선을 그리기 위해 3개의 점이 필요한데
<br> moveTo()로 한 개의 점을 찍고 quadraticCurveTo()으로 두 개의 점을 찍는다.
- 3차 베지에 곡선 : bezierCurveTo()

5-1. 2차 베지에곡선의 순환 알고리즘
```
2차베지에곡선(A,B,C){
// A: 시작점, B: 제어점, C: 종료점
D <- 선분 AB의 중점;
E <- 선분 BC의 중점;
F <- 선분 DE의 중점;
F는 베지에 곡선상의 한 점이 됨;
2차베지에곡선(A,D,F);
2차베지에곡선(F,E,C);
}
```

5-2. 2차 베지에 곡선 그리기
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
context.moveTo(50,150);
context.quadraticCurveTo(130,50,180,180);
context.stroke();
</script>
```

5-3. 3차 베지에 곡선 그리기
```html
<script>
let context = document.getElementById("myCanvas").getContext("2d");
context.moveTo(30,50);
context.bezierCurveTo(50,180,130,180,180,50);
/*bezierCurveTo() 로 3개 점의 좌표를 찍는다.*/
context.stroke();
</script>
```