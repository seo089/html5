# HTML5 요소

## 웹 폼

```html
<!DOCTYPE html>
<html>
    <head>
        <title>회원가입 폼</title>
    </head>
    <body>
        <h3>회원 정보 입력</h3>
        <form action="url" method="post">
        <p><label>회원 이름 : <input type="text" name="name"></label></p>
        <p><label>아이디 : <input type="text" name="id"></label></p>
        <p><label>비밀번호 : <input type="password" name="pwd"></label></p>
        <p><label>메일주소 : <input type="email" name="email"></label></p>
        <p><label>전화번호 : <input type="text" name="tel1" size="3" maxlength="3" value="010">
                            -<input type="text" name="tel2" size="4" maxlength="4">
                            -<input type="text" name="tel3" size="4" maxlength="4">
        </label></p>
        <p><label>직업 : <select size="1" name="job">
                            <option selected>학생</option>
                            <option>회사원</option>
                            <option>프로그래머</option>
                            <option>무직</option>
                        </select></label></p>
        <fieldset>
            <legend>성별</legend>
            <label><input type="radio" name="gender" value="male">남자</label>
            <label><input type="radio" name="gender" value="female">여자</label>
        </fieldset>
        <label>생년월일 : <input type="date" name="date"></label><br><br>
        <label>자기소개서 작성 :<br>
        <textarea rows="3" cols="40" name="intro">자기소개 입력</textarea></label>
        <p>
        <input type="submit" value="등록하기"> &nbsp;&nbsp;
        <input type="reset" value="초기화"></p>  
    </form>
    </body>
</html>
```

### form 요소

|속성|설명|
|:---:|:---|
|autocomplete="on or off"|자동완성 기능의 사용 여부를 지정|
|novalidate|submit 할 때 form 데이터의 유효성을 검사하지 않도록 지정|
|enctype="인코딩"|method="post" 경우 submit 할 때 form 데이터의 인코딩 방식 지정|

### HTML5에 추가된 type 속성값의 종류
|속성값|설명|
|:---:|:---|
|search|검색어 입력 <input type="search" ...>|
|tel|전화번호 입력 <input type="tel" ...>|
|url|url 입력 **자동으로 유효성 검사** <input type="url" ...>|
|email|email 입력 **자동으로 유효성 검사** <input type="email"[multiple] ...>|
|number|특정 범위의 숫자 입력<br> <input type="number" [min="최소값" max="최대값" step="유효입력간격" value="초기값"] ...>|
|range|특정 범위의 숫자 입력 *슬라이더 형태* <br> <input type="range" [min="최소값" max="최대값" step="유효입력간격" value="초기값"] ...>|
|color|색상 입력 <input type="color" ...>|
|date pickers| date : 날짜 (년,월,일 입력) <br> month : 연도/월 입력 <br> week : 연도, 주차 입력 <br> time : 시간을 입력하는 컨트롤 생성 <br> datetime-local : 날짜와 시간 입력

## HTML5에서 적용 의미가 변경된 요소
- b 요소
<br>주로 단어의 중요성을 표시할 때 사용되어 왔는데,
<br>HTML5 사양에 따르면 b요소는 강조의 의미가 없어지고 단순히 진하게 표시하는 수단이 됨


- i 요소
<br>HTML4.01에서는 기울어진 이탤릭체로 표시함으로 b 태그와 유사하게 강조 또는 중요성을 나타냈지만
<br>아래 시멘틱 요소로 대체할 수 없을 경우 한정적으로 사용하는 것을 권장함

|용도|요소|
|:---:|:---:|
|헤딩(제목)|h1 ~ h6|
|강조하는 텍스트|em|
|중요한 텍스트|strong|
|두드러진, 강조된 텍스트|mark|
|정의 용어|dfn|

- cite 요소
<br>기존 HTML에서는 이탤릭체로 표시하여 인용을 나타내는 용도였으나
<br>HTML5에서는 작품(책, 노래, 영화, 그림, 조각 등)의 제목을 나타내는 용도로 사용

- hr 요소
<br>기존 HTML에서는 단순히 수평선을 표시하기 위해 사용
<br>HTML5에서는 페이지에 내에서 주제가 변경되어 컨텐츠를 구분하는 *의미론적인* 용도로 사용
<br>기존 모든 속성은 css를 사용해 표현하도록 HTML5에서는 제거됨

- address 요소
<br>기존 HTML에서는 footer 요소 안에 이름, 이메일, 전화번호 등을 표시하는 용도
<br>HTML5에서는 실제 우편물 주소로 사용
<br> `article`요소가 추가되어 연락처 정보가 문서 저자의 것인지, 해당 article 저자의 것인지 의미론적으로 구분 가능

- s 요소
<br>기존에는 취소선으로 대체되거나 삭제된 텍스트를 표시하는 용도
<br>HTML5에서는 의미가 재정의되어 더이상 정확하지 않거나 관련이 없는 텍스트를 표시하기 위해 사용
<br>대체되거나 삭제된 텍스트를 표시하려면 `del` 요소를 사용한다.

- a 요소
<br>기존 HTML에서는 하이퍼링크나 앵커를 나타냈지만
<br>HTML5에서는 항상 하이퍼링크이며 href 속성을 사용하지 않으면 하이퍼링크의 표시자로 사용
<br>* name 속성은 더이상 지원 안함
<br>** download와 media 속성 추가 됨

- u 요소
<br>기존 밑줄 친 텍스트를 정의하기 위해 사용했던 것을
<br>HTML5에서 철자가 틀린 단어나 중국어의 고유명사와 같이 일반 텍스트와 스타일이 다른 텍스트를 표시하도록 재정의
<br>*하이퍼링크와 혼란을 야기하기 때문에 사용을 자제하도록 하고 있음*

- strong 요소
<br>기존에는 진하게 표시하여 강조하는 용도였으나 HTML5에서는 **중요한 텍스트**를 나타내기 위해 사용

- small 요소
<br>기존에는 단순히 텍스트를 작게 표시하는 용도로 사용
<br>HTML5에서는 작게 표시해야하는 부수적 해설이나 이용 조건, 법적 공지 등을 나타내는데 사용