# VS Code에서 Git LFS 실행하기

## 1. Git LFS 설치 확인

### 1) VS Code 실행

### 2) 터미널 열기

-   단축키: Ctrl + \` (백틱)
-   또는 상단 메뉴 → Terminal → New Terminal

### 3) Git LFS 설치 확인

``` bash
git lfs version
```

정상 설치되어 있으면 버전이 표시됩니다.

------------------------------------------------------------------------

## 2. Git LFS 초기 설정 (처음 1회만 실행)

``` bash
git lfs install
```

해당 PC에서 한 번만 실행하면 됩니다.

------------------------------------------------------------------------

## 3. LFS로 파일 추적하기

예: .mp4 파일을 LFS로 관리

``` bash
git lfs track "*.mp4"
```

`.gitattributes` 파일이 생성됩니다.

반드시 함께 커밋하세요:

``` bash
git add .gitattributes
git commit -m "Add gitattributes for LFS"
```

------------------------------------------------------------------------

## 4. 파일 추가 및 Push

### 터미널 사용

``` bash
git add large_file.mp4
git commit -m "Add file via Git LFS"
git push origin main
```

Push 시 자동으로 LFS 서버에 업로드됩니다.

### VS Code GUI 사용

1.  Source Control 탭 클릭
2.  변경 파일 Stage
3.  Commit 메시지 입력
4.  Push

------------------------------------------------------------------------

## 5. Clone 후 LFS 파일 다운로드

보통 clone 시 자동 다운로드됩니다.

만약 파일이 비어 있다면:

``` bash
git lfs pull
```

------------------------------------------------------------------------

## 6. LFS 파일 확인

``` bash
git lfs ls-files
```

------------------------------------------------------------------------

## 7. 자주 발생하는 문제 해결

### 1) 100MB 초과로 push 실패

LFS track 없이 먼저 커밋한 경우

``` bash
git lfs migrate import --include="*.mp4"
```

⚠ 히스토리 변경 → force push 필요

### 2) LFS 파일이 포인터 텍스트로만 보이는 경우

``` bash
git lfs pull
```

### 3) 다른 PC에서 파일이 안 받아질 때

``` bash
git lfs install
git lfs pull
```

------------------------------------------------------------------------

## 8. 협업 시 주의사항

-   팀원 모두 `git lfs install` 실행
-   `.gitattributes` 반드시 커밋
-   대용량 파일은 병합 충돌 위험 높음
-   GitHub LFS 용량 주기적 확인

------------------------------------------------------------------------

작성일: 2026
