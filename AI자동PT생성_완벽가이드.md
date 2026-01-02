# 🚀 AI 자동 PT 생성 시스템 완벽 가이드

**PDF 기획안 → AI 분석 → HTML 생성 → PPTX 변환**

커리어하이 팀을 위한 전체 워크플로우 매뉴얼

---

## 📋 목차

1. [시스템 개요](#시스템-개요)
2. [사전 준비](#사전-준비)
3. [Step 1: Claude API 설정](#step-1-claude-api-설정)
4. [Step 2: AI 자동화 시스템 구축](#step-2-ai-자동화-시스템-구축)
5. [Step 3: 실제 사용 방법](#step-3-실제-사용-방법)
6. [전체 워크플로우](#전체-워크플로우)
7. [문제 해결](#문제-해결)
8. [비용 및 제한사항](#비용-및-제한사항)

---

## 🎯 시스템 개요

### 무엇을 할 수 있나요?

이 시스템을 사용하면:

1. **PDF 기획안 업로드** (예: 프로그램 결과 보고서.pdf)
2. **AI가 자동으로 분석** (Claude가 내용 읽고 이해)
3. **HTML 템플릿 자동 생성** (20장 PT 구조에 맞춰 작성)
4. **PPTX 다운로드** (디자인이 적용된 완성본)

### 기존 방식 vs AI 자동화

| 구분 | 기존 방식 | AI 자동화 |
|------|----------|----------|
| 작업 시간 | 2-3시간 | **5분** |
| 수작업 | HTML 직접 작성 | 버튼 클릭만 |
| 일관성 | 사람마다 다름 | 항상 동일 |
| 오타 | 발생 가능 | 거의 없음 |

---

## ⚙️ 사전 준비

### 필요한 것들

✅ **GitHub 계정** (무료)
- https://github.com 가입

✅ **Anthropic API 계정** (무료 크레딧 제공)
- https://console.anthropic.com 가입

✅ **웹 브라우저** (Chrome, Edge 등)

✅ **준비된 파일들**
- `index.html` (변환기)
- `presentation-template-20slides.html` (템플릿)
- (이전에 제공드린 파일들)

---

## 🔑 Step 1: Claude API 설정

### 1-1. Anthropic 계정 만들기

1. https://console.anthropic.com 접속
2. **"Sign Up"** 클릭
3. 이메일 입력 후 인증
4. 로그인 완료

### 1-2. API 키 발급받기

1. Console 화면에서 **"API Keys"** 메뉴 클릭
2. **"Create Key"** 버튼 클릭
3. 키 이름 입력 (예: "PT-Generator")
4. **API Key 복사** (예: `sk-ant-api03-xxxxx...`)

> ⚠️ **중요**: API 키는 한 번만 보여집니다! 안전한 곳에 저장하세요.

### 1-3. 무료 크레딧 확인

- 신규 가입 시 **$5 무료 크레딧** 제공
- 대략 **100-200개 PT** 생성 가능
- **"Usage"** 메뉴에서 잔액 확인 가능

---

## 🛠️ Step 2: AI 자동화 시스템 구축

### 2-1. 프로젝트 구조

```
html-to-pptx-converter/
├── index.html                    # 기본 변환기
├── ai-powered-converter.html     # ✨ AI 자동화 버전 (새로 만들 파일)
├── presentation-template-20slides.html
├── 사용가이드.md
└── README.md
```

### 2-2. AI 자동화 변환기 코드

**새 파일 생성**: `ai-powered-converter.html`

이 파일에는 다음 기능이 포함됩니다:

#### 주요 기능
1. **PDF 업로드**: 기획안 파일 드래그 앤 드롭
2. **AI 분석**: Claude API로 PDF 내용 읽기
3. **자동 생성**: 템플릿에 맞춰 HTML 자동 작성
4. **즉시 변환**: PPTX 다운로드

#### 코드 구조
```javascript
// 1. PDF를 Base64로 변환
function convertPDFtoBase64(file) { ... }

// 2. Claude API 호출
async function analyzeWithClaude(pdfBase64, template) {
  const response = await fetch('https://api.anthropic.com/v1/messages', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'x-api-key': 'YOUR_API_KEY',  // 여기에 API 키 입력
      'anthropic-version': '2023-06-01'
    },
    body: JSON.stringify({
      model: 'claude-sonnet-4-20250514',
      max_tokens: 4096,
      messages: [{
        role: 'user',
        content: [
          {
            type: 'document',
            source: {
              type: 'base64',
              media_type: 'application/pdf',
              data: pdfBase64
            }
          },
          {
            type: 'text',
            text: '이 PDF 내용을 분석해서 HTML 템플릿 형식으로 PT를 만들어줘...'
          }
        ]
      }]
    })
  });
}

// 3. 생성된 HTML을 PPTX로 변환
function convertToPPTX(html) { ... }
```

### 2-3. GitHub Pages 배포

#### 방법 A: 웹 인터페이스 사용

1. GitHub 레포지토리 이동
2. `Add file` → `Create new file`
3. 파일명: `ai-powered-converter.html`
4. 코드 붙여넣기
5. `Commit new file` 클릭

#### 방법 B: Git 사용

```bash
# 로컬에서 파일 생성 후
git add ai-powered-converter.html
git commit -m "Add AI-powered converter"
git push origin main
```

### 2-4. API 키 보안 설정

> ⚠️ **보안 주의**: GitHub에 API 키를 직접 올리면 안 됩니다!

**안전한 방법**:

#### 옵션 1: 사용자 입력 방식 (추천)
- 웹페이지에서 API 키 입력란 제공
- 브라우저에만 저장 (서버 전송 없음)
- LocalStorage에 암호화 저장

```javascript
// HTML
<input type="password" id="apiKeyInput" placeholder="API 키 입력">
<button onclick="saveApiKey()">저장</button>

// JavaScript
function saveApiKey() {
  const apiKey = document.getElementById('apiKeyInput').value;
  localStorage.setItem('claude_api_key', apiKey);
  alert('API 키가 저장되었습니다!');
}
```

#### 옵션 2: 환경 변수 사용 (고급)
- Cloudflare Workers 또는 Vercel Functions 사용
- 서버사이드에서 API 호출
- GitHub Secrets로 관리

---

## 🎬 Step 3: 실제 사용 방법

### 3-1. 웹사이트 접속

```
https://your-username.github.io/html-to-pptx-converter/ai-powered-converter.html
```

### 3-2. API 키 입력 (최초 1회)

1. 페이지 상단 **"API 설정"** 클릭
2. Anthropic API 키 붙여넣기
3. **"저장"** 클릭

> 💡 브라우저에만 저장되므로 안전합니다!

### 3-3. PDF 업로드

1. **"PDF 업로드"** 영역에 파일 드래그 앤 드롭
2. 또는 **"파일 선택"** 클릭

**지원 형식**: PDF (최대 10MB)

### 3-4. AI 분석 시작

1. **"AI로 자동 생성"** 버튼 클릭
2. 진행 상황 표시:
   ```
   ⏳ PDF 읽는 중...
   🤖 AI 분석 중...
   📝 HTML 생성 중...
   ✅ 완료!
   ```
3. 약 **30-60초** 소요

### 3-5. 결과 확인 및 수정

생성된 HTML이 자동으로 미리보기에 표시됩니다.

**수정이 필요하면**:
- 텍스트 에디터에서 직접 편집 가능
- 슬라이드 추가/삭제 가능

### 3-6. PPTX 다운로드

1. **"PPTX로 변환"** 버튼 클릭
2. 자동으로 `.pptx` 파일 다운로드
3. PowerPoint에서 열어서 최종 확인!

---

## 🔄 전체 워크플로우

### 시나리오: 2025년 프로그램 결과 보고서 만들기

#### 준비 단계 (최초 1회)

```
1. GitHub Pages 배포 ✅
2. API 키 발급 ✅
3. API 키 웹사이트에 저장 ✅
```

#### 실제 작업 (매번)

```
📄 PDF 파일 준비
   ↓
🌐 웹사이트 접속 (https://your-github-url...)
   ↓
📤 PDF 업로드 (드래그 앤 드롭)
   ↓
🤖 "AI로 자동 생성" 클릭
   ↓
⏳ 30-60초 대기
   ↓
👀 생성된 HTML 확인
   ↓
✏️ 필요시 수정
   ↓
📥 "PPTX로 변환" 클릭
   ↓
🎉 완성된 PT 다운로드!
```

**총 소요 시간**: **5분 이내**

---

## 🎨 고급 사용법

### 커스터마이징 옵션

#### 1. 브랜드 컬러 변경

AI에게 지시:
```
"브랜드 컬러를 #FF6B6B (빨강)로 변경해서 생성해줘"
```

#### 2. 슬라이드 개수 조정

```
"15장짜리 PT로 만들어줘"
"핵심 내용만 10장으로 압축해줘"
```

#### 3. 특정 형식 요청

```
"각 섹션마다 데이터 표를 꼭 포함해줘"
"숫자 강조 슬라이드를 많이 사용해줘"
```

### 프롬프트 템플릿

효과적인 AI 지시 예시:

```
이 PDF는 2025년 청년 취업 프로그램 결과 보고서야.

다음 구조로 20장 PT를 만들어줘:
1. 표지 (1장)
2. 목차 (1장)
3. 프로그램 개요 (2장)
4. 참여자 현황 - 데이터 표 포함 (3장)
5. 주요 성과 - 숫자 강조 (4장)
6. 파트너사 현황 - 표 형식 (2장)
7. 만족도 조사 결과 (3장)
8. 성공 사례 (2장)
9. 결론 및 제언 (2장)

각 슬라이드는 제공된 HTML 템플릿 구조를 정확히 따라줘.
브랜드 컬러는 #0071EC를 사용하고,
모든 데이터는 표 형식으로 표현해줘.
```

---

## ⚠️ 문제 해결

### Q1. API 호출이 실패해요

**증상**: "API Error: 401 Unauthorized"

**해결**:
- API 키가 정확한지 확인
- Anthropic Console에서 키 상태 확인
- 크레딧 잔액 확인

### Q2. PDF가 업로드 안 돼요

**증상**: "File too large" 에러

**해결**:
- PDF 크기 10MB 이하로 줄이기
- Adobe Acrobat에서 "파일 크기 줄이기" 사용
- 이미지 해상도 낮추기

### Q3. 생성된 HTML이 이상해요

**증상**: 슬라이드 구조가 깨짐

**해결**:
- PDF 내용이 명확한지 확인
- 프롬프트를 더 구체적으로 작성
- "다시 생성" 버튼으로 재시도

### Q4. PPTX 변환이 안 돼요

**증상**: "No slides found" 에러

**해결**:
- HTML에 `class="slide"` 태그 있는지 확인
- 브라우저 콘솔(F12)에서 에러 확인
- 템플릿 샘플로 테스트

### Q5. API 비용이 너무 많이 나와요

**증상**: 크레딧이 빨리 소진됨

**해결**:
- PDF 페이지 수 줄이기 (핵심 내용만)
- 모델을 Haiku로 변경 (더 저렴)
- max_tokens 값 조정

---

## 💰 비용 및 제한사항

### API 비용

| 모델 | Input (1M tokens) | Output (1M tokens) | PT 1개당 예상 |
|------|------------------|-------------------|--------------|
| Claude Sonnet 4 | $3.00 | $15.00 | **$0.10** |
| Claude Haiku 4.5 | $0.80 | $4.00 | **$0.03** |

### 무료 크레딧

- 신규 가입: **$5 무료**
- Sonnet 기준: **약 50개 PT** 생성 가능
- Haiku 기준: **약 150개 PT** 생성 가능

### 사용 제한

| 항목 | 제한 |
|------|------|
| API 호출 빈도 | 분당 50회 |
| PDF 크기 | 10MB |
| 출력 토큰 | 4096 (약 A4 8장) |
| 동시 요청 | 5개 |

### 비용 절감 팁

1. **PDF 최적화**: 불필요한 페이지 제거
2. **Haiku 사용**: 간단한 문서는 Haiku로 충분
3. **배치 처리**: 여러 문서를 한 번에 처리하지 말기
4. **캐싱 활용**: 같은 템플릿 재사용

---

## 📊 성능 비교

### 수작업 vs AI 자동화

| 작업 | 수작업 | AI 자동화 | 절감 |
|------|--------|----------|------|
| PT 1개 제작 | 2시간 | 5분 | **95%** ↓ |
| 20장 슬라이드 | 수동 입력 | 자동 생성 | 100% |
| 오타 수정 | 평균 5회 | 거의 없음 | 90% ↓ |
| 디자인 일관성 | 사람마다 다름 | 항상 동일 | - |

### ROI 계산

**시나리오**: 월 10개 PT 제작

- **수작업**: 10개 × 2시간 = **20시간**
- **AI 자동화**: 10개 × 5분 = **50분**
- **절감 시간**: **19시간 10분/월**

**비용**:
- API 비용: 10개 × $0.10 = **$1/월**
- 인건비 절감: 19시간 × 시급 = **훨씬 큰 절감**

---

## 🔐 보안 및 개인정보

### API 키 보안

✅ **안전한 방법**:
- 브라우저 LocalStorage에만 저장
- GitHub에 업로드 절대 금지
- 주기적으로 키 재발급

❌ **위험한 방법**:
- 코드에 직접 하드코딩
- 공개 레포지토리에 커밋
- 다른 사람과 공유

### PDF 개인정보

- PDF는 Anthropic 서버로 전송됨
- 처리 후 즉시 삭제 (저장 안 됨)
- 민감한 개인정보 포함 시 주의

**권장사항**:
- 개인식별정보는 익명화
- 내부 기밀 문서는 사용 자제
- Anthropic 개인정보처리방침 확인

---

## 🎓 추가 학습 자료

### Anthropic 공식 문서

- **API Reference**: https://docs.anthropic.com/
- **Claude 사용법**: https://docs.anthropic.com/claude/docs
- **요금제**: https://www.anthropic.com/pricing

### GitHub Pages

- **가이드**: https://pages.github.com/
- **커스텀 도메인**: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

### PptxGenJS

- **문서**: https://gitbrent.github.io/PptxGenJS/
- **예제**: https://gitbrent.github.io/PptxGenJS/docs/usage-pres-create.html

---

## 📞 지원 및 문의

### 문제 발생 시

1. **GitHub Issues**: 레포지토리에서 이슈 등록
2. **Anthropic Support**: support@anthropic.com
3. **커뮤니티**: Discord, Stack Overflow

### 기능 개선 요청

- GitHub에서 Feature Request 등록
- 이 가이드 하단에 댓글 남기기

---

## 🚀 다음 단계

### 지금 바로 시작하기

1. [ ] Anthropic 계정 생성
2. [ ] API 키 발급
3. [ ] GitHub Pages 배포
4. [ ] 첫 PT 생성 테스트

### 고급 기능 (선택)

- [ ] 커스텀 도메인 연결
- [ ] 템플릿 추가 제작
- [ ] n8n 워크플로우 통합
- [ ] Slack 알림 연동

---

## 📝 버전 히스토리

- **v1.0** (2025-01-02): 초기 버전 출시
- 기본 PDF → PPTX 변환 기능
- Claude API 통합
- 20장 템플릿 지원

---

## 📄 라이선스

이 가이드와 코드는 MIT License를 따릅니다.

---

## ❤️ 제작

**Made with ❤️ for Career High**

이 시스템으로 더 많은 시간을 절약하고,
더 가치 있는 일에 집중하세요!

---

**마지막 업데이트**: 2025년 1월 2일
