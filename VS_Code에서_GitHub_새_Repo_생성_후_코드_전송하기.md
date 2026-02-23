# VS Code에서 GitHub의 새로운 Repo 생성 후 코드 전송하기

아래 순서대로 하면 **새 GitHub 저장소 생성 → VS Code 프로젝트
업로드(push)** 까지 완료됩니다.

------------------------------------------------------------------------

## 1. GitHub에서 새 Repository 생성

1.  GitHub 로그인
2.  우측 상단 **+ → New repository**
3.  Repository 이름 입력
4.  Public / Private 선택
5.  **Create repository** 클릭

⚠️ README / .gitignore는 체크하지 않는 것을 권장 (초기 push 충돌 방지)

------------------------------------------------------------------------

## 2. VS Code에서 프로젝트 폴더 열기

1.  VS Code 실행
2.  **File → Open Folder**
3.  업로드할 프로젝트 폴더 선택

------------------------------------------------------------------------

## 3. Git 저장소 초기화 (처음이라면)

VS Code 터미널에서 실행:

``` bash
git init
```

------------------------------------------------------------------------

## 4. 파일 추가 및 첫 커밋

``` bash
git add .
git commit -m "Initial commit"
```

------------------------------------------------------------------------

## 5. GitHub 원격 저장소 연결

GitHub에서 생성한 저장소 URL 복사 후 아래 실행:

``` bash
git remote add origin https://github.com/USERNAME/REPO_NAME.git
```

확인:

``` bash
git remote -v
```

------------------------------------------------------------------------

## 6. 기본 브랜치 main 설정

``` bash
git branch -M main
```

------------------------------------------------------------------------

## 7. GitHub로 업로드 (Push)

``` bash
git push -u origin main
```

성공하면 GitHub에서 코드 확인 가능 🎉

------------------------------------------------------------------------

## 8. 전체 명령어 한 번에 정리

``` bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/USERNAME/REPO_NAME.git
git branch -M main
git push -u origin main
```

------------------------------------------------------------------------

## 9. 자주 발생하는 오류 해결

### 1) remote origin already exists

``` bash
git remote remove origin
git remote add origin https://github.com/USERNAME/REPO_NAME.git
```

### 2) rejected (fetch first)

GitHub에서 README를 먼저 생성한 경우:

``` bash
git pull origin main --allow-unrelated-histories
git push origin main
```

### 3) 인증 오류

-   VS Code에서 GitHub 로그인 필요
-   또는 Personal Access Token 사용

------------------------------------------------------------------------

## 10. Git LFS 사용하는 경우

Push 전에:

``` bash
git lfs install
```

확장자 추적:

``` bash
git lfs track "*.mp4"
git add .gitattributes
git commit -m "Add Git LFS tracking"
```

------------------------------------------------------------------------

작성일: 2026
