# skiils-for-teachers

한국 학교 교사를 위한 **Claude Code 스킬** 모음입니다.

공문서 정리, 인수인계서 작성 등 학교 행정 업무를 자동화합니다.

## 포함된 스킬

| 스킬 | 설명 |
|------|------|
| **document-organizer** | 공문서 파일을 공문번호별로 자동 분류하여 폴더로 정리 |
| **handover-generator** | 공문서 파일명을 분석하여 업무 인수인계서를 자동 생성 |

## 설치 방법

### 1. 이 리포지토리 다운로드

PowerShell을 열고 아래 명령어를 실행합니다:

```powershell
git clone https://github.com/slowly007-beep/skiils-for-teachers.git
```

### 2. 원하는 스킬을 복사

**document-organizer 설치:**

```powershell
Copy-Item -Recurse skiils-for-teachers\skills\document-organizer $env:USERPROFILE\.claude\skills\
```

**handover-generator 설치:**

```powershell
Copy-Item -Recurse skiils-for-teachers\skills\handover-generator $env:USERPROFILE\.claude\skills\
```

**둘 다 설치:**

```powershell
Copy-Item -Recurse skiils-for-teachers\skills\* $env:USERPROFILE\.claude\skills\
```

설치가 끝나면 Claude Code를 재시작합니다. 추가 설정은 필요 없습니다.

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
