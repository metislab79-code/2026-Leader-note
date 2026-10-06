# 간부수첩 · Vercel 바로 배포판

설치 및 서버 빌드가 필요 없는 정적 사이트 완성본입니다.
60개 업무, 교육 실습, 현업 활용, 프롬프트 복사, AI 서비스 열기,
답변 붙여넣기, Word 저장과 브라우저 작업 저장을 유지합니다.

## 1. GitHub에 올리기

1) 이 ZIP을 압축 해제합니다. ZIP 파일 자체를 업로드하지 마세요.
2) 가장 간단한 방법은 새 GitHub 저장소를 만드는 것입니다.
   예: Leader-note-Vercel
3) Add file → Upload files에서 압축을 푼 폴더 안의 파일과 assets 폴더를 올립니다.
4) Commit changes를 누릅니다.

저장소 첫 화면에 아래 파일이 바로 보여야 합니다.
- index.html
- vercel.json
- assets/ (CSS와 JavaScript)
- metislab-logo.jpg
- favicon.svg

상위 폴더째 올려 index.html이 한 단계 안에 들어가지 않게 해 주세요.
.openai 폴더는 필요하지 않습니다. .vercelignore는 안내문 등을 게시에서 제외하는 선택 파일입니다.

## 2. Vercel에 배포하기

1) Add New → Project에서 위 GitHub 저장소를 Import합니다.
2) Framework Preset이 표시되면 Other를 선택합니다.
3) Root Directory는 저장소 최상위(기본값)로 둡니다.
4) Deploy를 누릅니다.

vercel.json이 설치와 빌드를 건너뛰고 최상위 파일을 게시하도록 설정합니다.
별도 npm/pnpm 설치나 API 키, 환경변수는 필요하지 않습니다.

설정값을 직접 확인할 경우:
- Framework Preset: Other
- Root Directory: 저장소 최상위
- Install Command: 비움 (설치 생략)
- Build Command: 비움 (빌드 생략)
- Output Directory: . (마침표 한 개)

## 기존 저장소와 Vercel 프로젝트를 계속 쓰려면

기존 소스를 먼저 백업한 뒤, 이전 배포 파일을 이 ZIP 내용으로 교체하세요.
특히 package.json, pnpm-lock.yaml, pnpm-workspace.yaml, next.config.ts,
vite.config.ts, 기존 vercel.json과 이전 .github 배포 workflow를 함께 남기지 마세요.
이 완성본에서는 해당 빌드 설정을 사용하지 않습니다.
새 vercel.json을 저장소 최상위에 둡니다.
Vercel에서 Root Directory가 source 또는 docs로 지정되어 있으면 최상위로 되돌립니다.
이후 최신 커밋을 Redeploy하세요. 이전 빌드 캐시는 사용하지 않는 편이 좋습니다.
기존 파일을 지우기 어렵다면 새 저장소에 이 완성본만 올리는 것이 가장 간단합니다.

## 동작 방식과 업데이트

- AI 연결은 프롬프트를 복사해 ChatGPT·Gemini·Claude에 붙여넣는 방식입니다.
- 서버 AI API 기능은 포함하지 않습니다.
- 저장한 업무는 각 사용자의 브라우저에 남습니다.
- 이전 사이트의 작업은 작업 백업으로 내려받은 뒤 새 사이트에서 불러오세요.
- 이 폴더는 빌드된 완성본입니다. 소스 수정 시에는 새로 빌드한 파일을 교체해야 합니다.
- GitHub Pages용 ZIP 및 Cloudflare용 ZIP과 섞지 마세요.

## 검증 범위

원본 정적 앱의 TypeScript 검사 및 프로덕션 빌드 통과.
이번 패키지의 HTML·CSS·JavaScript·이미지 경로와 ZIP 무결성 확인.
사용자의 GitHub/Vercel 프로젝트에는 직접 접근하지 않았으므로 실제 배포 성공은 확인하지 않았습니다.
오류가 계속되면 Vercel Build Logs의 첫 오류 메시지와 Root Directory 설정을 전달해 주세요.

Vercel 공식 설정 안내:
https://vercel.com/docs/project-configuration/vercel-json
