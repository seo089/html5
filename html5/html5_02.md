# HTML 요소

## 레이아웃을 위한 시멘틱 요소
기존 HTML이 표현 위주였다면, HTML5는 **의미 중점적인 요소**가 추가되었다.

|요소|설명|
|:---:|---|
|header|머릿말을 나타내는 요소|
|hgroup|제목과 부제목을 묶어서 나타내는 요소|
|nav|메뉴 영역을 나타내는 요소|
|section|제목별로 나눌 수 있는 문서의 콘텐츠 영역을 구성하는 요소|
|article|개별 콘텐츠를 나타내는 요소|
|aside|좌우측의 사이드 영역을 나타내는 요소|
|footer|꼬리말을 나타내는 요소|

## 시멘틱 인라인 요소
인라인 요소 : 텍스트의 일부에 대해서 마크업 하는 텍스트 요소 (기존에 이어붙음)

- mark 요소
<br> 시각적, 의미적으로 특정 문구 또는 단어를 강조
<br> 노란색 형광펜으로 표시되는데 css로 스타일 변경 가능
```html
<mark>mark 태그 : 노란색으로 표시</mark>
```
- time 요소
<br> 시간이나 날짜 표현에 의미를 부여할 때 사용
```html
<p>
오전 <time> 07:00 </time> 기상합니다. time 태그는 화면상에는 변화가 없습니다.
</p>
<p>
대략적인 날짜를 표현할 때 <time datetime="2020-08-11">8월 중순</time> 으로<br>
표시 할 수 있습니다.
</p>
```
- meter 요소
<br> 일정 범위 안의 측정값이나 분포 비율 등을 나타낼 때 사용
    - meter 요소의 속성

    |속성|설명|
    |:---:|---|
    |value|실제로 측정한 데이터 값(required)|
    |min,max|meter 요소가 인식하는 최소값(0.0)과 최대값(1.0)|
    |low,high|허용되는 범위의 최소값과 최대값|
    |optinum|최적의 기대치|
```html
<p>과제 진행률 <meter max="100" value="80"></meter></p>
```

- progress 요소
<br> 작업의 현재 진행 상태를 나타낼 때 사용 (파일의 복사, 다운로드 시 작업의 진행 정도 표시 등)
<br> **점진적적으로 변하는 양**을 나타내므로 반드시 **자바스크립트**와 연동해서 업데이트 해야함
```html
progress 요소 표현 : <progress value="25" max="100"></progress>
```

- ruby 요소
<br> 하나 이상의 구문 콘텐츠에 루비 주석을 표시할 때 사용
<br> * 일본어/한자의 기본 문자열 주변에 발음법, 의미를 나타내기 위해 추가하는 짧은 텍스트
    - rt 요소 : 루비 주석을 구성하는 루비 텍스트 표시
    - rp 요소 : 루비 주석을 지원하지 않은 웹브라우저를 위해 사용 (괄호로 표시)
```html
<ruby>한자 기재<rt>루비 표시</rt></ruby>
```
 
- wbr 요소 (word break opportunity)
<br> 실제 줄바꿈이 수행되는 것이 아니라 레이아웃 배치 상황에 따라 바뀌어도 좋은 지점을 미리 지정하는 것
<br> 반응형 웹 등에서 사용

## 시멘틱 블록 요소 
블록 요소 : 문서 구조적 요소로 블록 단위로 적용되는 요소 (새로운 행에 표현)

- main 요소
<br> 주요 콘텐츠 블록을 지정할 때 사용
<br> 문서에서 유일한 부분이므로 반복적으로 사용되는 컨텐츠는 포함할 수 없음
<br> 전체적인 아웃라인에는 아무런 영향을 주지 않는다.
```html
<body>
    <main> 
    <h3>블록 요소</h3>
        <p>main 요소</p>
        <article>
            <p>main은 article, aside, footer, header, nav 하위 요소로 사용할 수 없다.</p>
        </article>
    </main>
</body>
```

- figure 요소, figcaption 요소
    - figure 요소 : 본문에 삽입된 그림, 다이어그램, 사진, 소스코드, 동영상 등과 같은 독립적 콘텐츠를 블록화 할때 사용
    - figcaption 요소 : figure 요소에 대한 캡션(제목)을 표시하는 것, figure 요소 바로 다음이나 맨 마지막에 작성
    
```html
<figure>
    <img src="test.jpg" width="200" height="100">
    <figcaption>figure test</figcaption>
</figure>
```

- details 요소, summary 요소
    - details 요소 : 사용자가 핸들을 클릭해서 세부정보를 보게 만들 수 있음
    - summary 요소 : details 하위 요소로 핸들에 표시되는 제목
```html
<details>
    <summary>summary 태그 </summary>
    <p> 디테일 밑에 내용 작성</p>
</details>
<details open> <!--open 속성을 사용하면 세부정보가 처음부터 보여진다-->
    <summary>summary 태그 </summary>
    <p> 디테일 밑에 내용 작성</p>
</details>
```
