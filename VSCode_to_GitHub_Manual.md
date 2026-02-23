# VS Code에서 폴더를 GitHub로 업로드하는 방법

## ✅ 준비사항

1.  Git 설치 확인\
    터미널에서:

        git --version

    버전이 나오면 OK

2.  VS Code에서 GitHub 로그인 (권장)

------------------------------------------------------------------------

# 📌 방법 1: 버튼만으로 업로드 (가장 쉬운 방법)

## 1단계: 폴더 열기

-   VS Code 실행
-   File → Open Folder
-   업로드할 폴더 선택

## 2단계: Git 초기화

-   왼쪽 Source Control(가지 아이콘) 클릭
-   "Initialize Repository" 클릭

## 3단계: 커밋하기

-   메시지 입력칸에:

        first commit

-   Commit 클릭

## 4단계: GitHub로 업로드

-   "Publish to GitHub" 클릭
-   Public 또는 Private 선택
-   업로드 완료

------------------------------------------------------------------------

# 📌 방법 2: 특정 GitHub 주소로 업로드

## 1단계: Commit 완료

## 2단계: 터미널 열기

Terminal → New Terminal

## 3단계: 원격 저장소 연결

    git remote add origin https://github.com/USERNAME/REPO.git

## 4단계: 브랜치 맞추고 업로드

    git branch -M main
    git push -u origin main

------------------------------------------------------------------------

# 📌 자주 발생하는 오류 해결

### remote already exists

    git remote set-url origin https://github.com/USERNAME/REPO.git

### failed to push (원격에 README가 이미 있는 경우)

    git pull origin main --rebase
    git push

------------------------------------------------------------------------

# 📌 권장 .gitignore 설정

## Python 프로젝트

    .venv/
    __pycache__/
    .env

## Node 프로젝트

    node_modules/
    dist/
    .env

------------------------------------------------------------------------

작성일: 자동 생성 문서
