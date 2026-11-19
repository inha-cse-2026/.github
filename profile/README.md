👋 Welcome to inhacse average

웹 프로젝트와 PS(Problem Solving) 공부를 함께 기록하는 공간입니다. 처음 오셨다면 아래 규칙을 한 번 읽고 시작해 주세요. 모두 같은 규칙으로 쓰면 누가 봐도 바로 이해할 수 있는 저장소가 됩니다.

<br>
📌 목차
레포지토리 종류와 이름 규칙
웹 프로젝트 README 작성 규칙
PS 레포지토리 구조
브랜치 전략
커밋 컨벤션
Pull Request 규칙
작업 흐름 한눈에 보기
주의 사항
<br>
1. 레포지토리 종류와 이름 규칙
종류	이름 형식	예시
웹 백엔드	Backend_{프로젝트명}	Backend_TodoApp, Backend_StudyMatching
웹 프론트엔드	Frontend_{프로젝트명}	Frontend_TodoApp, Frontend_StudyMatching
PS(알고리즘)	PS_{이름 또는 팀명}	PS_gildong, PS_Study2026
프로젝트명은 PascalCase(단어 첫 글자만 대문자, 띄어쓰기 없음)로 씁니다.
같은 서비스의 백엔드와 프론트엔드는 프로젝트명을 똑같이 맞춥니다. (Backend_TodoApp ↔ Frontend_TodoApp)
레포지토리 About(설명) 칸에 프로젝트를 한 줄로 소개해 주세요.
<br>
2. 웹 프로젝트 README 작성 규칙

모든 Backend_ / Frontend_ 레포지토리의 README에는 아래 항목이 반드시 들어가야 합니다.

항목	필수	내용
프로젝트 주제	✅	무엇을 만드는지, 왜 만드는지
팀원	✅	누구와 함께하는지, 각자 맡은 역할
기술 스택	✅	사용한 언어, 프레임워크, DB, 도구
개발 기간	⭕	시작일부터 종료일까지
실행 방법	⭕	다른 사람이 clone해서 바로 실행할 수 있는 명령어
폴더 구조	⭕	주요 디렉터리 설명
관련 레포	⭕	짝이 되는 Backend / Frontend 레포 링크
📄 README 템플릿 (복사해서 사용하세요)
markdown
# {프로젝트명}

## 📖 프로젝트 소개
- 주제: 
- 목적: 
- 개발 기간: 2026.00.00 ~ 2026.00.00

## 👥 팀원
| 이름 | 역할 | GitHub |
|---|---|---|
| 홍길동 | Backend (로그인, 게시판 API) | [@아이디](https://github.com/아이디) |
| 김태현| Frontend (메인 페이지, UI) | [@아이디](https://github.com/아이디) |

## 🛠 기술 스택
- Language: 
- Framework: 
- Database: 
- Tools: Git, GitHub, Notion, Figma

## 🚀 실행 방법
```bash
git clone https://github.com/{조직명}/{레포명}.git
cd {레포명}
# 설치 및 실행 명령어
```

## 📁 폴더 구조
```
src/
├── controller/   # 요청 처리
├── service/      # 비즈니스 로직
└── repository/   # DB 접근
```

## 🔗 관련 레포지토리
- Backend: 
- Frontend:
<br>
3. PS 레포지토리 구조

PS 레포지토리는 개념 공부(research) 와 문제 풀이(solution) 를 나눠서 정리합니다.

PS_{이름}/
├── README.md
├── research/                     # 자료구조 · 알고리즘 개념 정리
│   ├── data-structure/
│   │   ├── stack.md
│   │   ├── queue.md
│   │   └── heap.md
│   └── algorithm/
│       ├── dfs-bfs.md
│       ├── dynamic-programming.md
│       └── binary-search.md
└── solution/                     # 백준 문제 풀이 코드 + 해설
    ├── bronze/
    │   └── BOJ_1000_A+B/
    │       ├── BOJ_1000.py       # 풀이 코드
    │       └── README.md         # 풀이 해설
    ├── silver/
    └── gold/
폴더 이름은 research와 solution으로 통일합니다.
문제 폴더 이름은 BOJ_{문제번호}_{문제이름} 형식으로 씁니다.
solution 아래는 티어별(bronze, silver, gold)로 나눕니다. 팀에서 원하면 유형별(dp, graph, greedy 등)로 나눠도 되지만, 한 레포 안에서는 한 가지 방식만 씁니다.
📄 풀이 해설 템플릿 (solution/.../README.md)
markdown
# [BOJ 1000] A+B

- 문제 링크: https://www.acmicpc.net/problem/1000
- 난이도: Bronze V
- 분류: 수학, 구현

## 💡 접근 방법
어떻게 생각했고 왜 이 알고리즘을 골랐는지 적습니다.

## ⏱ 복잡도
- 시간: O( )
- 공간: O( )

## 📝 회고
틀렸던 이유, 새로 알게 된 점, 다른 사람 풀이와 비교한 내용
<br>
4. 브랜치 전략

main은 언제나 실행 가능한 완성본입니다. 작업은 항상 새 브랜치에서 하고, PR로 검토를 받은 뒤 main에 합칩니다.

main
feature/login
fix/header
init
feat: 로그인 UI
feat: 로그인 API 연동
PR #1
fix: 헤더 깨짐 수정
PR #2
브랜치	용도	예시
main	배포 및 최종본 (직접 push ❌)	main
feature/{기능}	새 기능 개발	feature/login, feature/board-crud
fix/{내용}	버그 수정	fix/header-layout
refactor/{내용}	코드 정리	refactor/auth-service
docs/{내용}	문서 작업	docs/readme
브랜치 이름은 소문자와 하이픈(-) 으로 씁니다.
기능 하나에 브랜치 하나를 만듭니다.
브랜치는 되도록 1~3일 안에 PR을 올려 합칩니다. 오래 붙잡고 있을수록 충돌이 커집니다.
개인 PS 레포는 혼자 쓰므로 main에 바로 커밋해도 괜찮습니다.
<br>
5. 커밋 컨벤션
형식
{타입}: {무엇을 했는지}
타입 목록
타입	의미	예시
feat	새 기능	feat: 로그인 폼 UI 추가
fix	버그 수정	fix: 비밀번호 빈칸일 때 에러 수정
refactor	동작은 그대로, 코드 정리	refactor: 인증 로직 함수로 분리
style	포맷, 세미콜론 등 (로직 변경 없음)	style: 들여쓰기 통일
docs	문서	docs: README 실행 방법 추가
test	테스트 코드	test: 회원가입 API 테스트 추가
chore	설정, 패키지, 빌드	chore: eslint 설정 추가
remove	파일 삭제	remove: 사용하지 않는 이미지 삭제
PS 레포 전용
타입	의미	예시
solve	문제 풀이 추가	solve: [BOJ 1000] A+B
docs	개념 정리 (research)	docs: [자료구조] 스택 개념 정리
refactor	기존 풀이 개선	refactor: [BOJ 1260] BFS 풀이 시간 단축
작성 규칙
제목은 50자 이내로 쓰고, 끝에 마침표를 찍지 않습니다.
하나의 커밋에는 하나의 변경만 담습니다. 기능 추가와 오타 수정은 따로 커밋합니다.
설명이 더 필요하면 제목 아래에 한 줄을 비우고 본문을 씁니다.
관련 이슈가 있으면 번호를 붙입니다. 예: feat: 게시글 작성 API 추가 (#12)
❌ 이런 메시지는 쓰지 않습니다: 수정, ㅇㅇ, final, 진짜최종
<br>
6. Pull Request 규칙
PR 제목은 커밋과 같은 형식으로 씁니다. 예: feat: 로그인 기능 구현
팀원 1명 이상이 승인(Approve)해야 merge할 수 있습니다.
리뷰 중에 수정 요청을 받으면 같은 브랜치에 커밋하고 push합니다. PR에 자동으로 반영됩니다.
merge한 브랜치는 삭제합니다.
리뷰는 코드에 대해 하고, 사람을 평가하지 않습니다. 예: "이 부분은 함수로 분리하면 읽기 쉬울 것 같아요!"
📄 PR 템플릿
markdown
## 📝 작업 내용
- 

## ✅ 확인 방법
1. 

## 📸 스크린샷 (UI 변경 시)

## 🔗 관련 이슈
- closes #

💡 레포지토리에 .github/pull_request_template.md 파일로 넣어 두면 PR을 열 때마다 이 양식이 자동으로 채워집니다.

<br>
7. 작업 흐름 한눈에 보기
bash
# 1) 최신 main 받기 (작업 시작 전에 항상!)
git switch main
git pull origin main

# 2) 작업 브랜치 만들기
git switch -c feature/login

# 3) 의미 단위로 커밋
git add .
git commit -m "feat: 로그인 폼 UI 추가"

# 4) 원격 저장소에 올리기
git push -u origin feature/login

# 5) GitHub에서 Pull Request 생성 → 리뷰 → Merge

# 6) 정리
git switch main
git pull origin main
git branch -d feature/login
<br>
8. 주의 사항
🔒 .env, API 키, 비밀번호는 절대 커밋하지 않습니다. 실수로 올렸다면 바로 팀에 알리고 키를 새로 발급받습니다.
📦 node_modules/, build/, .idea/, __pycache__/ 같은 파일은 .gitignore에 등록합니다. (gitignore.io에서 쉽게 만들 수 있어요)
🛡 웹 프로젝트 레포는 Settings → Branches에서 main 브랜치 보호 규칙을 켜서 PR 없이 push하지 못하게 합니다.
❓ 모르는 게 있으면 혼자 고민하지 말고 Issue나 Discussion에 질문해 주세요!
<br>
<p align="center">Happy Coding! 🚀</p>
