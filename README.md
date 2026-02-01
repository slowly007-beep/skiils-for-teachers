# skiils-for-teachers

한국 학교 교사를 위한 **Claude Code 스킬** 모음입니다.

공문서 정리, 인수인계서 작성 등 학교 행정 업무를 자동화합니다.

## 포함된 스킬

| 스킬 | 설명 |
|------|------|
| **document-organizer** | 공문서 파일을 공문번호별로 자동 분류하여 폴더로 정리 |
| **handover-generator** | 공문서 파일명을 분석하여 업무 인수인계서를 자동 생성 |

## 설치 방법

두 가지 방법 중 편한 것을 선택하세요.

---

### 방법 A: 직접 다운로드 (터미널 없이)

**1단계.** 이 페이지 상단의 초록색 **`<> Code`** 버튼 → **`Download ZIP`** 클릭

**2단계.** 다운로드된 ZIP 파일을 압축 해제

**3단계.** 압축 해제한 폴더 안의 `skills` 폴더를 엽니다. 그 안에 `document-organizer`, `handover-generator` 폴더가 있습니다.

**4단계.** 원하는 스킬 폴더를 아래 경로에 복사합니다:

```
C:\Users\{본인 사용자명}\.claude\skills\
```

> **`.claude` 폴더가 안 보인다면:** 파일 탐색기 상단 메뉴에서 **보기 → 숨긴 항목** 체크를 켜세요.
>
> **`.claude` 폴더 자체가 없다면:** Claude Code를 한 번이라도 실행하면 자동 생성됩니다.

**5단계.** Claude Code를 재시작하면 설치 완료!

---

### 방법 B: 터미널 사용

**1단계. PowerShell 열기**

`Win + X` 를 누른 뒤 **"터미널"** 또는 **"Windows PowerShell"** 을 클릭합니다.

> 명령 프롬프트(cmd)가 열렸다면 아래 명령어가 약간 다릅니다. PowerShell을 권장합니다.

**2단계. 리포지토리 다운로드**

```powershell
git clone https://github.com/slowly007-beep/skiils-for-teachers.git
```

**3단계. 스킬 복사**

document-organizer 설치:

```powershell
Copy-Item -Recurse skiils-for-teachers\skills\document-organizer $env:USERPROFILE\.claude\skills\
```

handover-generator 설치:

```powershell
Copy-Item -Recurse skiils-for-teachers\skills\handover-generator $env:USERPROFILE\.claude\skills\
```

둘 다 한번에 설치:

```powershell
Copy-Item -Recurse skiils-for-teachers\skills\* $env:USERPROFILE\.claude\skills\
```

**4단계.** Claude Code를 재시작하면 설치 완료!

---

## 사용법

### document-organizer (공문서 자동 분류)

Claude Code에서 다음과 같이 말하면 됩니다:

- `"공문서 정리해줘"` — 공문서를 공문번호별 폴더로 자동 분류
- `"공문 경로 변경"` — 정리 대상 폴더를 변경

**처음 실행하면** AI가 공문서 폴더 경로를 물어봅니다. 한 번 알려주면 이후에는 자동으로 기억합니다.

**필요 사항:** [Node.js](https://nodejs.org/) 설치 필요

**정리 전:**
```
공문 모음\
├── (인창고등학교-22206 (본문)) [제출] AI 중점학교 운영 신청.pdf
├── (인창고등학교-22206 (첨부)) [붙임1] 신청서.hwpx
├── (인창고등학교-22206 (첨부)) [붙임2] 계획서.hwpx
├── (인창고등학교-568 (본문)) [제출] 디지털튜터.pdf
└── (인창고등학교-568 (첨부)) [붙임1] 명단.xlsx
```

**정리 후:**
```
공문 모음\
├── (인창고등학교-22206 (본문)) [제출] AI 중점학교 운영 신청\
│   ├── (인창고등학교-22206 (본문)) [제출] AI 중점학교 운영 신청.pdf
│   ├── (인창고등학교-22206 (첨부)) [붙임1] 신청서.hwpx
│   └── (인창고등학교-22206 (첨부)) [붙임2] 계획서.hwpx
└── (인창고등학교-568 (본문)) [제출] 디지털튜터\
    ├── (인창고등학교-568 (본문)) [제출] 디지털튜터.pdf
    └── (인창고등학교-568 (첨부)) [붙임1] 명단.xlsx
```

### handover-generator (인수인계서 자동 생성)

- `"인수인계서 작성해줘"` — 공문 폴더를 분석하여 마크다운 인수인계서 생성
- `"공문 분석해줘"` — 공문 분류 결과만 확인
- `"인수인계서 검증해줘"` — 기존 인수인계서와 공문 목록 교차 검증

파일 내용은 열지 않으며, **파일명만으로** 업무를 분류하고 인수인계서를 작성합니다.

출력은 **노션 Import 호환 마크다운** (.md) 형식입니다.

## 대상 파일명 패턴

이 스킬들은 한국 공공기관 전자문서시스템(업무관리시스템)에서 내보낸 공문서 파일명을 기준으로 동작합니다:

```
(기관명-공문번호 (본문)) 문서 제목.pdf
(기관명-공문번호 (첨부)) [붙임1] 첨부 제목.hwpx
```

## 라이선스

MIT License
