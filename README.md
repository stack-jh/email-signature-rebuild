# UNION biometrics Email Signature Builder

GitHub Pages용 정적 이메일 서명 생성기. 서버 불필요.

## 구성
| 파일 | 용도 |
|---|---|
| `index.html` | 직원용 — 이름·직책·연락처 입력, 주소(국문/영문/병기)·배너(국문/영문/없음) 선택 |
| `admin.html` | 관리자용 — 회사 공통값 편집 후 config.json 생성 |
| `config.json` | 회사 공통 설정 (로고·배너·주소·SNS·아이콘 URL) |
| `sig-core.js` | 서명 HTML 생성 공통 로직 |
| `icons/` | 연락처 아이콘 폴백 (tel/mobile/email/home/addr) |

## 배포
1. 이 폴더 전체를 리포지토리에 업로드 (Public)
2. Settings → Pages → Source: Deploy from a branch / Branch: main / (root) → Save
3. 직원 공유 주소: `https://stack-jh.github.io/email-signature-rebuild/`
4. 관리자 주소: `https://unionbioai-collab.github.io/email-signature/admin.html`

## 회사 공통값 변경 (관리자)
admin.html 열기 → 값 수정 → "config.json 다운로드" →
리포지토리에 Add file → Upload files로 config.json 덮어쓰기 커밋 → 1~2분 내 전 직원 반영

## 서명 템플릿 사양
- 이름(국문+영문 병기) 18pt bold / 부서 | 직책 (#003da6)
- 헤더 하단 구분선: 브랜드 블루 #003da6
- 연락처: T / M / E / 홈페이지(고정) / A — 자사 호스팅 아이콘
- 주소: 국문 · 영문 · 병기 선택
- 하단 배너: 국문(email_kor.gif) · 영문(email-eng.gif) · 미사용 선택
- 로고: 수직 중앙 정렬, 110px

## 아이콘/이미지 교체
모든 아이콘과 로고는 config.json의 https URL로 지정됩니다.
주의: sftp:// 경로는 업로드용일 뿐 이메일·브라우저에서 열리지 않으므로 반드시 https URL 사용.

## CES 2027 및 Instagram 기능
- 회사 로고 좌측 / 연락처 중앙 / CES 2027 최고혁신상 배지 우측 표시(관리자 페이지에서 URL 변경 또는 미표시 가능)
- Instagram은 국문 채널로, 직원이 표시 여부를 직접 선택하며 기본값은 미표시
- 배지 및 Instagram PNG는 이 GitHub 저장소의 assets/ 디렉터리에 호스팅
- GitHub Pages 사용 시 https://stack-jh.github.io/email-signature-rebuild/ 주소가 배포되도록 Pages 설정 필요

## CES 이메일 배너 선택
- 디자인: CES 수상형(흰 배경), CES 기술 강조형(블루 배경). 기존 회사소개 배너도 선택할 수 있습니다.
- 언어: 국문, 영문, 사용 안 함. 주소 언어와 독립적으로 선택합니다.
- 각 CES 배너의 원본은 1200×300px, 서명에서는 600×150px로 출력합니다.
- 회사 CI와 LiveGuard 로고는 제공된 원본을 사용하고, CES 배지는 CES 공식 수상 페이지의 원본을 사용합니다. 로고를 AI로 다시 그리거나 색상·비율을 변경하지 않습니다.
- 관리자에서 네 가지 배너 이미지 URL과 CES 배너 클릭 링크를 수정하고 디자인·언어별로 미리 볼 수 있습니다.
- 기존 `bannerKo` / `bannerEn` 값은 유지합니다. `bannerDesign`이 없는 이전 호출도 기존 배너를 출력합니다.
