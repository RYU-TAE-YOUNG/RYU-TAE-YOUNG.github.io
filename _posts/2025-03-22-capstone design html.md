# 웹 개발 가이드: HTML & CSS 기초

이번 포스트에서는 HTML과 CSS의 기본 개념을 이해하고, 웹페이지를 확장하는 방법에 대해 알아봅니다. 각 섹션별로 자세한 설명과 함께 예시 코드도 제공하니, 직접 실습해 보시기 바랍니다.

---

## 2.1 HTML 기본개념

### 2.1.1 HTML 소개
- **정의:** HTML은 HyperText Markup Language의 약자로, 웹페이지의 구조와 내용을 작성하는 마크업 언어입니다.
- **역할:** 웹 브라우저가 HTML 문서를 해석해 사용자에게 내용을 시각적으로 표현할 수 있도록 돕습니다.

### 2.1.2 HTML 문서 구조
- **DOCTYPE 선언:** 문서가 HTML5 표준을 따름을 알리기 위해 `<!DOCTYPE html>`로 시작합니다.
- **HTML 태그:** `<html>` 태그로 전체 문서를 감싸며, 시작과 종료를 명시합니다.
- **head 섹션:** `<head>` 태그 안에는 문서의 메타데이터(문서 제목, 문자 인코딩, 외부 파일 링크 등)가 포함됩니다.
- **body 섹션:** `<body>` 태그 안에는 실제 화면에 표시될 내용(텍스트, 이미지, 링크 등)이 위치합니다.

### 2.1.3 주요 HTML 태그
- **제목 태그:** `<h1>` ~ `<h6>` (문서의 계층적 제목 구성)
- **문단 태그:** `<p>` (문단 구분)
- **링크 태그:** `<a>` (다른 페이지 또는 외부 사이트와 연결)
- **이미지 태그:** `<img>` (이미지 삽입)
- **리스트 태그:** `<ul>`, `<ol>`, `<li>` (순서 있는/없는 목록 구성)

### 2.1.4 시맨틱 태그
- **의미 부여:** `<header>`, `<nav>`, `<section>`, `<article>`, `<footer>`와 같은 태그를 사용해 문서의 각 부분에 의미를 부여합니다.
- **이점:** 검색 엔진 최적화(SEO)와 접근성을 개선하는 데 도움을 줍니다.

---

## 2.2 HTML 목록, 테이블, 폼 & 웹페이지 확장하기

### 2.2.1 HTML 목록
- **순서 있는 목록:** `<ol>` 태그로 숫자나 알파벳 순서의 목록을 생성합니다.
- **순서 없는 목록:** `<ul>` 태그로 불릿 포인트 목록을 생성합니다.
- **목록 항목:** `<li>` 태그를 사용해 각 항목을 나열합니다.

### 2.2.2 HTML 테이블
- **기본 구조:** `<table>` 태그로 시작하며, `<tr>` 태그로 행(row)을, `<td>` 태그로 데이터 셀을 구성합니다.
- **헤더 셀:** `<th>` 태그를 사용하여 열의 제목을 표시합니다.
- **테이블 캡션:** `<caption>` 태그로 테이블의 제목을 추가할 수 있습니다.

### 2.2.3 HTML 폼
- **폼 태그:** `<form>` 태그를 사용하여 사용자 입력을 받는 영역을 만듭니다.
- **입력 요소:** `<input>` (텍스트, 체크박스, 라디오 등), `<textarea>` (멀티라인 텍스트), `<select>` (드롭다운 메뉴), `<button>` (버튼) 등을 활용합니다.
- **폼 속성:** 
  - `action`: 폼 데이터가 전송될 URL을 지정합니다.
  - `method`: 데이터 전송 방식(GET, POST 등)을 결정합니다.
- **검증 및 처리:** 클라이언트 및 서버 사이드 검증을 통해 사용자 입력의 정확성을 보장합니다.


### 2.2.4 웹페이지 확장하기
- **멀티미디어 요소:** 이미지(`<img>`), 오디오(`<audio>`), 비디오(`<video>`) 등 다양한 미디어를 활용하여 풍부한 콘텐츠 제공.
- **링크 및 내비게이션:** `<a>` 태그를 사용해 외부 페이지 및 사이트로의 이동을 구현합니다.
- **외부 콘텐츠 임베딩:** 유튜브 동영상, 지도 등 외부 서비스를 페이지 내에 포함시켜 사용자 경험을 향상합니다.

---

## 2.3 CSS 기본 개념 & 웹페이지 스타일링

### 2.3.1 CSS 소개
- **정의:** CSS(Cascading Style Sheets)는 HTML 요소의 시각적 스타일(색상, 레이아웃, 폰트 등)을 지정하는 스타일 시트 언어입니다.
- **목적:** 웹페이지 디자인의 일관성과 미적 감각을 향상시키며, 콘텐츠와 스타일을 분리하여 관리합니다.

### 2.3.2 CSS 선택자
- **태그 선택자:** 예) `p { }`, `div { }`
- **클래스 선택자:** 예) `.classname { }` – 여러 요소에 공통 스타일 적용
- **아이디 선택자:** 예) `#idname { }` – 특정 요소에만 스타일 적용
- **속성 선택자:** 예) `[type="text"] { }` – 특정 속성을 가진 요소 선택
- **복합 선택자:** 자손, 자식, 형제 선택자를 활용해 보다 구체적인 요소 지정

### 2.3.3 CSS 속성 및 박스 모델
- **텍스트 스타일:** `color`, `font-size`, `font-family`, `text-align` 등을 사용해 텍스트를 꾸밉니다.
- **박스 모델:** 
  - **margin:** 요소 외부 여백
  - **border:** 요소 테두리
  - **padding:** 요소 내부 여백
  - **width/height:** 요소의 너비와 높이 설정
- **배경 스타일:** `background-color`, `background-image`로 요소 배경을 설정합니다.

### 2.3.4 CSS 적용 방법
- **내부 스타일시트:** HTML `<head>` 내 `<style>` 태그로 직접 작성.
- **외부 스타일시트:** 별도의 `.css` 파일을 만들어 `<link>` 태그로 연결.
- **인라인 스타일:** HTML 요소 내 `style` 속성을 사용해 직접 스타일 적용.

### 2.3.5 반응형 웹 디자인
- **미디어 쿼리:** 화면 크기나 디바이스 특성에 따라 다른 스타일을 적용합니다.
- **유동적 레이아웃:** `width: 100%`, `max-width` 등으로 다양한 화면에 맞게 요소 크기를 조정합니다.
- **플렉스 박스 및 그리드:** CSS Flexbox와 Grid를 사용해 복잡한 레이아웃을 쉽게 구성합니다.

---

HTML과 CSS의 기본 개념을 확실히 익히면, 더 복잡하고 다양한 웹페이지를 제작할 수 있는 탄탄한 기초를 다질 수 있습니다. 앞으로도 실습 예제와 심화 내용을 통해 웹 개발 실력을 한층 더 높여보시길 바랍니다.

<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>202016222 통계학과 류태영의 웹페이지</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
    <h1>안녕하세요! 저는 [202016222 통계학과 류태영]입니다.</h1>
    <p>이것은 저의 첫 번째 HTML 웹페이지입니다.</p>
    <div class="img-container">
        <img src="https://enook.jbnu.ac.kr/files/329/tyoung612345@gmail.com/5.JPG" alt="내 사진" style="width:300px; height:auto;">
    </div>
    
    <!-- 관심 목록 -->
    <h2>관심 목록</h2>
    <ul class="interest-list">
        <li>경제</li>
        <li>주식</li>
        <li>축구</li>
        <li>정치</li>
    </ul>

    <!-- 프로필 정보 -->
    <h2>프로필 정보</h2>
    <table class="profile-table">
        <tr>
            <th>항목</th>
            <th>내용</th>
        </tr>
        <tr>
            <td>이름</td>
            <td>류태영</td>
        </tr>
        <tr>
            <td>학번</td>
            <td>202016222</td>
        </tr>
        <tr>
            <td>학과</td>
            <td>통계학과</td>
        </tr>
        <tr>
            <td>취미</td>
            <td>경제, 주식, 축구, 정치</td>
        </tr>
    </table>

    <!-- 추가 정보 링크 -->
    <h2>더 많은 정보</h2>
    <div class="links">
        <a href="https://www.mt.co.kr/">머니투데이</a>
        <a href="https://www.edaily.co.kr/">이데일리</a>
        <a href="https://www.youtube.com/@SPOTV/">SPOTV</a>
        <a href="https://www.youtube.com/@MBCNEWS11/">MBC</a>
    </div>

    <!-- 메시지 입력 폼 -->
    <h2>메시지 보내기</h2>
    <form action="https://formspree.io/f/xoveqwqv" method="POST">
        <fieldset>
            <legend>문의사항</legend>
            
            <label for="name">이름:</label>
            <input type="text" id="name" name="name" placeholder="이름을 입력하세요">

            <label for="email">이메일:</label>
            <input type="email" id="email" name="email" placeholder="이메일을 입력하세요">

            <label for="message">메시지:</label>
            <textarea id="message" name="message" rows="5" placeholder="문의사항을 입력하세요"></textarea>

            <!-- 추가 도전 과제: 버튼에 border-radius와 hover 효과 적용 -->
            <button type="submit">전송</button>
        </fieldset>
    </form>
</body>
</html>


