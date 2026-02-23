# Git LFS 사용 메뉴얼

## 1. Git LFS란?

Git LFS (Large File Storage)는 대용량 파일을 Git 저장소에서 효율적으로
관리하기 위한 확장 도구입니다.\
Git에는 실제 파일 대신 포인터(pointer) 파일만 저장하고, 실제 대용량
파일은 별도의 LFS 스토리지에 업로드됩니다.

------------------------------------------------------------------------

## 2. 설치 방법

### Mac

``` bash
brew install git-lfs
```

### Windows

https://git-lfs.com 에서 설치 파일 다운로드

### Linux (Ubuntu)

``` bash
sudo apt install git-lfs
```

설치 후 초기화:

``` bash
git lfs install
```

------------------------------------------------------------------------

## 3. 기본 사용법

### 1) 추적할 파일 설정

``` bash
git lfs track "*.mp4"
git lfs track "*.psd"
git lfs track "*.zip"
```

`.gitattributes` 파일이 생성됩니다.

### 2) 파일 추가 및 커밋

``` bash
git add .gitattributes
git add large_file.mp4
git commit -m "Add file via Git LFS"
git push origin main
```

### 3) LFS 파일 확인

``` bash
git lfs ls-files
```

### 4) 클론 후 파일 다운로드

``` bash
git lfs pull
```

------------------------------------------------------------------------

## 4. GitHub에서 LFS 용량 확인하는 방법

### 방법 1: Repository 기준 확인

1.  GitHub 저장소 접속
2.  Settings 클릭
3.  왼쪽 메뉴에서 "Packages" 또는 "Usage" 확인
4.  Git LFS Data 사용량 확인

### 방법 2: 계정 전체 사용량 확인

1.  GitHub 프로필 사진 클릭
2.  Settings → Billing and plans
3.  Git LFS Data 항목에서 Storage / Bandwidth 확인

무료 계정 기준: - Storage: 1GB - Bandwidth: 1GB / month

------------------------------------------------------------------------

## 5. Git LFS 에러 해결 방법

### 1) smudge filter lfs failed

``` bash
git lfs install --force
git lfs pull
```

### 2) LFS object missing

``` bash
git lfs fetch --all
git lfs pull
```

### 3) 403 또는 용량 초과 에러

-   GitHub Billing에서 LFS 사용량 확인
-   용량 초과 시 데이터팩 구매 필요

### 4) 이미 커밋된 대용량 파일 LFS로 변경

``` bash
git lfs migrate import --include="*.mp4"
```

⚠ 히스토리 변경이 발생하므로 force push 필요

------------------------------------------------------------------------

## 6. 협업 시 주의사항

1.  모든 팀원이 Git LFS 설치 필요
2.  `.gitattributes` 파일 반드시 커밋
3.  대용량 파일은 병합 충돌 발생 가능성 높음
4.  LFS 용량 모니터링 필수
5.  CI/CD 환경에서도 git lfs install 필요

------------------------------------------------------------------------

## 7. 자주 사용하는 명령어

  명령어                     설명
  -------------------------- -------------------
  git lfs track "\*.ext"     파일 추적
  git lfs untrack "\*.ext"   추적 해제
  git lfs ls-files           LFS 파일 목록
  git lfs pull               LFS 파일 다운로드
  git lfs prune              캐시 정리

------------------------------------------------------------------------

작성일: 2026
