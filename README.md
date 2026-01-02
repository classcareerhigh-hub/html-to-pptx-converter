# 📊 HTML to PPTX Converter

커리어하이 프레젠테이션 템플릿 변환 도구

## 🚀 빠른 시작

### 온라인에서 바로 사용
👉 **[여기를 클릭하세요](https://classcareerhigh-hub.github.io/html-to-pptx-converter/)**


## 📦 파일 구성

```
html-to-pptx-converter/
├── index.html                          # 변환기 메인 페이지
├── presentation-template-20slides.html # 20장 템플릿
├── 사용가이드.md                        # 상세 가이드
└── README.md                           # 이 파일
```

## 🎯 사용 방법

### 1. 템플릿 작성
`presentation-template-20slides.html` 파일을 열어서 내용을 수정합니다.

### 2. 변환
- 웹사이트 접속
- HTML 코드 붙여넣기
- "PPTX 파일로 변환하기" 클릭
- 자동 다운로드!

## 🌐 GitHub Pages 배포 방법

### STEP 1: 레포지토리 생성
1. GitHub에 로그인
2. 우측 상단 `+` 버튼 → `New repository`
3. Repository name: `html-to-pptx-converter`
4. Public 선택
5. `Create repository` 클릭

### STEP 2: 파일 업로드
```bash
# 방법 1: 웹에서 업로드
GitHub 레포지토리 페이지 → Add file → Upload files → 파일 드래그

# 방법 2: Git 사용
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/classcareerhigh-hub/html-to-pptx-converter.git
git push -u origin main
```

### STEP 3: GitHub Pages 활성화
1. 레포지토리 → `Settings` 탭
2. 왼쪽 메뉴 → `Pages`
3. Source: `Deploy from a branch`
4. Branch: `main` / `/ (root)` 선택
5. `Save` 클릭

### STEP 4: 배포 완료!
- 5분 정도 기다리면 자동 배포됩니다
- 접속 URL: `https://classcareerhigh-hub.github.io/html-to-pptx-converter/`

## 📱 노션 임베드 방법

노션 페이지에서:
```
/embed
```
입력 후 → GitHub Pages URL 붙여넣기

예시:
```
/embed https://classcareerhigh-hub.github.io/html-to-pptx-converter/
```

## ✨ 지원 기능

### 슬라이드 타입
- ✅ 표지 슬라이드
- ✅ 목차 슬라이드
- ✅ 섹션 구분
- ✅ 제목 + 본문
- ✅ 리스트
- ✅ 강조 박스
- ✅ **데이터 표** (3열, 4열)
- ✅ 숫자 강조
- ✅ 2단 레이아웃

### 디자인 요소
- 16:9 비율 자동 유지
- 브랜드 컬러 (#0071EC, #5050EF)
- 타이포그래피 계층 (H1 42pt, P 18pt)
- 표 스타일링 (파란 헤더)
- 슬라이드 번호 자동 표시

## 📋 HTML 작성 규칙

### 기본 구조
```html
<section class="slide" data-page="01">
  <h2>상위 제목</h2>
  <h1>메인 제목</h1>
  <p>본문 내용</p>
</section>
```

### 데이터 표
```html
<table>
  <thead>
    <tr>
      <th>항목</th>
      <th>값</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>데이터 1</td>
      <td>100</td>
    </tr>
  </tbody>
</table>
```

### 강조 박스
```html
<div class="key-box">
  중요한 메시지를 여기에
</div>
```

## 🛠️ 기술 스택

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Library**: PptxGenJS 3.12.0
- **Deployment**: GitHub Pages

## 📞 지원

문제가 발생하면 GitHub Issues에 등록해주세요.

## 📄 라이선스

MIT License

---

**Made with ❤️ for Career High**
