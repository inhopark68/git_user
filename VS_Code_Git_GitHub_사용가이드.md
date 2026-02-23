# VS Code Git & GitHub 사용 가이드

------------------------------------------------------------------------

## 1. VS Code에서 GitHub 로그인 연결 방법

### 방법 1: VS Code 계정 메뉴 사용

1.  VS Code 실행
2.  왼쪽 하단의 계정 아이콘 클릭
3.  "Sign in to GitHub" 선택
4.  브라우저가 열리면 GitHub 로그인
5.  인증 완료 후 VS Code로 자동 연결

### 방법 2: Command Palette 사용

1.  Ctrl + Shift + P
2.  "GitHub: Sign in" 입력 후 실행
3.  브라우저 인증 진행

로그인 확인 방법: - 왼쪽 하단 계정 아이콘에서 GitHub 계정 표시 확인

------------------------------------------------------------------------

## 2. 기존 프로젝트를 GitHub에 올리는 전체 과정

### 1단계: Git 저장소 초기화

``` bash
git init
```

### 2단계: 파일 추가 및 커밋

``` bash
git add .
git commit -m "Initial commit"
```

### 3단계: GitHub에서 새 Repository 생성

-   GitHub 접속
-   New Repository 클릭
-   Repository 이름 입력
-   Create repository 클릭

### 4단계: 원격 저장소 연결

``` bash
git remote add origin https://github.com/USERNAME/REPOSITORY_NAME.git
```

### 5단계: 브랜치 설정

``` bash
git branch -M main
```

### 6단계: GitHub로 업로드

``` bash
git push -u origin main
```

이제 GitHub에서 코드 확인 가능

------------------------------------------------------------------------

## 3. Git init vs Clone 차이 설명

  ------------------------------------------------------------------------
  항목            git init                  git clone
  --------------- ------------------------- ------------------------------
  목적            새 저장소 생성            기존 저장소 복사

  사용 시점       로컬 프로젝트를 처음 Git  이미 GitHub에 있는 프로젝트를
                  관리할 때                 가져올 때

  원격 연결       직접 remote 추가 필요     자동으로 origin 설정

  사용 예         기존 프로젝트를 GitHub에  팀 프로젝트 참여 시
                  올릴 때                   
  ------------------------------------------------------------------------

### git init 예시

``` bash
git init
```

→ 현재 폴더에 .git 생성

### git clone 예시

``` bash
git clone https://github.com/username/repo.git
```

→ 원격 저장소 전체 복사 + 자동 연결

------------------------------------------------------------------------

작성일: 2026
