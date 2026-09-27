# Assignment 2-2. HTML Form & JS (assign04-c01-22300272)

마켓컬리 회원가입 폼을 클론 코딩하면서, 순수 HTML 폼(form1.html) → CSS로 레이아웃을 입힌 폼(form1_css.html) → JS로 이메일 도메인 자동 입력과 제출 전 유효성 검사를 추가한 폼(form1_js.html) 순서로 단계적으로 발전시킨 과제입니다.

- **학번**: 22300272
- **이름**: 박동민

## Pages

| 페이지 | 설명 | URL |
|---|---|---|
| form1.html | 순수 HTML 회원가입 폼 (fieldset/legend로 구역 구분) | https://2026-oss-a04.vercel.app/form1.html |
| form1_css.html | form1을 복사해 CSS로 레이아웃·스타일 적용 | https://2026-oss-a04.vercel.app/form1_css.html |
| form1_js.html | form1_css를 복사해 JS(이메일 도메인 자동 입력, submit 검증) 추가 | https://2026-oss-a04.vercel.app/form1_js.html |

## Vercel Deploy URL
- https://2026-oss-a04.vercel.app/

## GitHub Repository
- **Repo URL**: https://github.com/2026-2-OSS/assign04-c01-22300272
- **Commit History**: https://github.com/2026-2-OSS/assign04-c01-22300272/commits/main/

## Development Flow

VS Code → Git → GitHub → Vercel

1. VS Code에서 코드 작성
2. Git으로 버전 관리 (add, commit)
3. GitHub에 push
4. Vercel에서 자동 배포

---

## Weekly Review

### Key Learning
이번 주 배운 핵심 내용 3가지

1. `<fieldset>`/`<legend>`, `<optgroup>`, `<label for>` 같은 요소로 폼을 의미 단위로 묶으면, 스타일이 없어도 구조가 읽히고 라벨을 눌러도 입력칸이 선택되는 등 사용성이 좋아진다는 것
2. 같은 HTML 구조를 유지한 채 CSS만 입혀도(form1 → form1_css) 화면이 완전히 달라진다는 것, 즉 구조(HTML)와 표현(CSS)을 분리해서 생각해야 한다는 것
3. `required`, `type="email"`, `minlength` 같은 HTML 네이티브 검증을 먼저 걸어두고, JS에서는 `checkValidity()`로 그 결과를 재사용하면 검증 규칙을 두 번 작성하지 않아도 된다는 것

### Form Elements
사용한 폼 요소와 각 용도

| 요소 | 사용한 곳 | 용도 |
|---|---|---|
| `<form>` | 전체 폼 (`id="userForm"`, `method="post"`) | 입력값을 한 번에 제출하는 컨테이너 |
| `<fieldset>` / `<legend>` | form1: 필수입력사항, 성별, 추가입력 사항, 이용약관동의 / form1_css·js: 필수입력사항 | 관련 입력들을 구역으로 묶고 구역 제목 표시 |
| `<label for>` | 모든 입력 항목 | 입력칸과 설명 텍스트 연결 (라벨 클릭 시 포커스) |
| `input type="text"` | 아이디, 이름, 주소, 추천인 아이디 | 일반 한 줄 텍스트 입력 |
| `input type="password"` | 비밀번호, 비밀번호확인 | 입력값을 가려서 표시 |
| `input type="email"` | 이메일 (form1_css / form1_js) | 이메일 형식 자동 검증 |
| `input type="tel"` | 휴대폰 | 전화번호 입력 (모바일에서 숫자 키패드) |
| `input type="date"` | 생년월일 | 날짜 선택기로 날짜 입력 |
| `input type="radio"` | 성별 (남자/여자/선택안함) | 여러 개 중 하나만 선택 (`name="gender"`로 그룹화) |
| `input type="checkbox"` | 약관 동의, 광고 수신 채널(문자/이메일/카카오) | 여러 개를 독립적으로 선택 |
| `<select>` / `<option>` | 이메일 도메인 | 정해진 목록에서 하나 선택 |
| `<optgroup>` | 이메일 도메인 ("자주 쓰는 도메인" / "기타") | select 옵션을 그룹으로 나눠 표시 |
| `<datalist>` | 주소 (form1.html, 서울/부산/포항) | 텍스트 입력에 자동완성 후보 제공 |
| `<textarea>` | 추가 요청사항(form1), 상세주소(form1_css / form1_js) | 여러 줄 텍스트 입력 |
| `<button type="button">` | 인증번호 받기, 주소 검색 | 제출하지 않는 보조 버튼 |
| `input type="submit"` | 가입하기 | 폼 제출 |

### HTML vs CSS
form1.html과 form1_css.html의 차이

- **form1.html (HTML only)**: 스타일 없이 브라우저 기본 모양. 줄바꿈을 `<br>`로 처리하고 구역은 4개의 `<fieldset>` 테두리로만 구분됨. 라벨과 입력칸이 위아래로 쌓이는 단순한 구조
- **form1_css.html (HTML + CSS)**: form1.html을 복사한 뒤 `<style>`을 추가하고, 각 항목을 `.row`(라벨) + `.row-content`(입력칸·버튼) 구조로 감싸 라벨과 입력칸이 한 줄에 나란히 오는 컬리 스타일 레이아웃으로 바꿈
  - `<br>` 대신 CSS 레이아웃으로 줄 정렬
  - 입력칸·버튼 크기, 테두리, 둥근 모서리, 포커스 시 테두리 색 등 시각 스타일 적용
  - 광고 수신 채널(문자/이메일/카카오) 체크박스를 들여쓰기해서 하위 항목임을 표시
- **구조 변경점**: CSS 버전에서는 이메일 `type="email" required`, 비밀번호 `minlength="6"`을 추가하고, 이메일 select에 "선택하기" 안내 옵션을 넣음. 또한 주소 datalist를 빼고 상세주소 textarea를 추가했으며, "추가입력 사항"(추천인 아이디/추가 요청사항) 구역은 제외함. 구역을 fieldset 4개로 나누던 방식 대신 fieldset 하나(`* 필수입력사항`) 안에 `.row`로 항목을 나열함
- **form1_css → form1_js**: 폼 본문(`<body>`~`</form>`)은 완전히 같고, CSS에 `:invalid:focus` 빨간 테두리 규칙 하나와 `<script>`만 추가함

### Validation & JS
**HTML 네이티브 검증**
- `required`: 아이디, 비밀번호, 비밀번호확인, 이름, 이메일, 생년월일, 필수 약관 3개(이용약관, 개인정보, 만 14세 이상)
- `type="email"`: 이메일 입력값이 `아이디@도메인` 형식인지 검사
- `minlength="6"`: 비밀번호·비밀번호확인 최소 6자
- CSS `input:invalid:focus`: 포커스된 입력칸이 유효하지 않으면 테두리를 빨간색으로 표시

**submit 이벤트 처리 과정 (form1_js.html)**
1. `form.addEventListener("submit", ...)`로 제출 이벤트를 가로챔
2. `form.querySelectorAll("[required]")`로 필수 항목을 모두 가져옴
3. 각 항목에 `field.checkValidity()`를 호출해 HTML에 선언된 규칙(required/type/minlength)을 통과하는지 확인
4. 하나라도 실패하면
   - `event.preventDefault()`로 제출을 막고
   - `alert("입력값을 다시 확인해주세요.")`로 알린 뒤
   - `field.focus()`로 문제가 있는 첫 번째 입력칸으로 커서를 옮기고
   - `return`으로 함수를 종료해 나머지 항목 검사와 완료 처리를 건너뜀
5. 모두 통과하면 실제 서버가 없으므로 `event.preventDefault()`로 페이지 이동을 막고 `alert("등록이 완료되었습니다.")` 표시

**이메일 도메인 자동 입력**
- `emailDomain`의 `change` 이벤트에서 "직접 입력"이 아니면 이메일 입력값의 `@` 앞부분만 남기고(`split("@")[0]`) 뒤에 `@` + 선택한 도메인을 붙임
- 이미 다른 도메인이 붙어 있어도 앞부분만 남기므로 도메인을 바꿔도 `@`가 중복되지 않음

### Problem & Solution
실습 중 발생한 문제와 해결 과정

- **문제**: 이메일 입력이 "아이디 입력칸 + @ + 도메인 select"로 나뉘어 있는데, 아이디 입력칸에 `type="email"`을 적용하니 `marketkurly`처럼 아이디만 입력한 상태에서는 `@`가 없어 브라우저 네이티브 검증에 항상 걸렸음. 화면상으로는 도메인을 select에서 골랐는데도 "이메일 형식이 아니다"라는 오류가 나서, 분리된 입력 구조와 `type="email"` 검증이 서로 맞지 않았음
- **해결**: 도메인 select에서 값을 고르는 순간 JS로 이메일 입력칸 값에 `@도메인`을 자동으로 붙이도록 해서, 입력칸 안의 값 자체가 완성된 이메일 주소가 되게 함. 그 결과 `type="email"` 검증과 submit 시 `checkValidity()`가 정상적으로 통과함. 또한 select에 기본값으로 `<option value="" selected disabled hidden>선택하기</option>`를 넣어, 페이지 로드 시 naver.com이 자동 선택된 것처럼 보이던 문제도 함께 정리함

### Reflection
새롭게 알게 된 점

- 유효성 검사를 JS로 처음부터 다 짜야 한다고 생각했는데, HTML 속성(`required`, `type`, `minlength`)만으로도 상당 부분이 해결되고 JS에서는 `checkValidity()`로 그 결과를 가져다 쓰기만 하면 된다는 점이 인상적이었다
- 같은 폼을 HTML → CSS → JS 순서로 복사하며 발전시키니, 각 단계에서 무엇이 바뀌는지(구조 / 표현 / 동작)가 분리되어 보여서 세 기술의 역할 차이를 체감할 수 있었다
- 화면에 보이는 UI 구조(아이디와 도메인 분리)와 브라우저가 검사하는 실제 값(입력칸 하나의 value)이 다를 수 있어서, 검증을 설계할 때는 "실제로 검사되는 값이 무엇인지"를 먼저 생각해야 한다는 것을 알게 됐다

## AI Usage
AI(Claude)를 활용해 과제 요구사항 점검, 이메일 입력 검증 문제 해결, README 작성을 진행함.

**이메일 도메인 자동 입력 (AI 활용 신규 학습)**
- **이메일 도메인 select 선택 시 값에 @가 없으면 자동으로 @도메인을 붙여주는 기능은 AI를 활용해서 새로 학습한 부분**입니다.
- `change` 이벤트, `split("@")[0]`로 기존 도메인을 잘라내는 방식, "직접 입력" 선택 시 `return`으로 건너뛰는 처리를 AI 설명을 통해 익히고 form1_js.html에 적용함

**요구사항 점검**
- form1 / form1_css / form1_js 세 파일이 복사-발전 관계로 구조가 일관적인지, 필수 항목에 `required`가 빠진 곳이 없는지 등을 코드와 대조받음
