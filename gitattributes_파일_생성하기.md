# .gitattributes 파일 생성하기

## 1. .gitattributes란?

`.gitattributes`는 Git에서 파일 처리 방식을 정의하는 설정 파일입니다.\
줄바꿈 방식 지정, 바이너리 처리, Git LFS 설정 등에 사용됩니다.

------------------------------------------------------------------------

## 2. 방법 1: Git LFS 명령으로 자동 생성 (권장)

``` bash
git lfs track "*.mp4"
```

명령 실행 시 프로젝트 루트에 `.gitattributes` 파일이 자동 생성됩니다.

예시 내용:

    *.mp4 filter=lfs diff=lfs merge=lfs -text

생성 후 반드시 커밋:

``` bash
git add .gitattributes
git commit -m "Add gitattributes for LFS"
```

------------------------------------------------------------------------

## 3. 방법 2: VS Code에서 직접 생성

### 1) 프로젝트 루트에 새 파일 생성

파일 이름:

    .gitattributes

### 2) 파일 내용 작성 예시

    # Git LFS 설정
    *.mp4 filter=lfs diff=lfs merge=lfs -text
    *.psd filter=lfs diff=lfs merge=lfs -text
    *.zip filter=lfs diff=lfs merge=lfs -text

### 3) 저장 후 커밋

``` bash
git add .gitattributes
git commit -m "Create .gitattributes"
```

------------------------------------------------------------------------

## 4. 주요 옵션 설명

  옵션         설명
  ------------ ---------------------------
  filter=lfs   Git LFS로 파일 처리
  diff=lfs     diff 비교 시 LFS 사용
  merge=lfs    병합 시 LFS 사용
  -text        텍스트 자동 변환 비활성화

------------------------------------------------------------------------

## 5. 파일 위치

프로젝트 루트에 생성해야 합니다:

    project-root/
     ├── .git/
     ├── .gitattributes
     ├── src/
     └── README.md

------------------------------------------------------------------------

## 6. 주의사항

-   반드시 프로젝트 루트에 위치해야 함
-   팀원과 공유하려면 커밋 필수
-   LFS 사용 시 `.gitattributes` 없으면 정상 동작하지 않음

------------------------------------------------------------------------

작성일: 2026
