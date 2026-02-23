# VS Code에서 기존 Git 설정 제거하기

기존 Git 설정 제거는 **어떤 것을 제거하려는지**에 따라 방법이 다릅니다.\
아래에서 원하는 경우를 선택해 진행하세요.

------------------------------------------------------------------------

## 1. 현재 프로젝트의 Git 저장소(.git) 제거하기

### ✅ 방법: `.git` 폴더 삭제

### VS Code 터미널 (Mac/Linux)

``` bash
rm -rf .git
```

### Windows PowerShell

``` powershell
Remove-Item -Recurse -Force .git
```

#### 확인

``` bash
git status
```

→ `not a git repository` 메시지 출력

------------------------------------------------------------------------

## 2. 원격 저장소(origin) 연결만 제거하기

Git 기록은 유지하고 GitHub 연결만 끊고 싶을 때

### 원격 확인

``` bash
git remote -v
```

### 원격 제거

``` bash
git remote remove origin
```

### 확인

``` bash
git remote -v
```

→ 출력 없음

------------------------------------------------------------------------

## 3. Git 사용자 설정 제거하기

### 현재 설정 확인

``` bash
git config --list
```

### 전역(Global) 사용자 정보 삭제

``` bash
git config --global --unset user.name
git config --global --unset user.email
```

### 로컬(Local) 사용자 정보 삭제

``` bash
git config --unset user.name
git config --unset user.email
```

------------------------------------------------------------------------

## 4. VS Code에서 GitHub 로그인 해제하기

1.  왼쪽 하단 **계정 아이콘** 클릭\
2.  GitHub 계정 옆 톱니바퀴 클릭\
3.  **Sign Out** 선택

또는 Command Palette 사용:

1.  Ctrl + Shift + P\
2.  `GitHub: Sign out` 실행

------------------------------------------------------------------------

## 5. Git 프로그램 자체를 완전히 제거하기

### Windows

-   제어판 → 프로그램 제거 → Git 삭제

### Mac (Homebrew 설치 기준)

``` bash
brew uninstall git
```

------------------------------------------------------------------------

## 6. 상황별 요약

  제거 대상                     방법
  ----------------------------- ----------------------------
  이 프로젝트 Git 기록만 삭제   `.git` 폴더 삭제
  GitHub 연결만 삭제            `git remote remove origin`
  사용자 정보 삭제              `git config --unset`
  VS Code 로그인 해제           GitHub Sign out
  Git 완전 삭제                 프로그램 제거

------------------------------------------------------------------------

작성일: 2026
