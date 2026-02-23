# 안드로이드용 제작 매뉴얼 (Vite + Capacitor 기반)

작성일: 2026-02-23

---

## 1. 문서 목적

본 문서는 Vite 기반 웹 프론트엔드 프로젝트를  
Android APK 및 AAB(App Bundle) 형태로 패키징하는 전체 절차를 설명합니다.

적용 대상:
- Vite 기반 SPA
- React / Vue / Vanilla JS 프로젝트
- Capacitor를 이용한 Android 앱 패키징

---

## 2. 전체 구성 구조

웹 프로젝트 (Vite)
        ↓ build (dist 생성)
Capacitor
        ↓ sync
Android Native Project (Gradle)
        ↓
APK / AAB 생성

---

## 3. 사전 준비 사항

### 필수 설치

1. Node.js (LTS 권장)
2. npm
3. Android Studio
4. Android SDK (Android Studio 최초 실행 시 자동 안내)

설치 확인:

```bash
node -v
npm -v
```

---

## 4. Capacitor 설치 및 초기화

프로젝트 루트에서 실행:

```bash
npm install @capacitor/core @capacitor/cli
npx cap init
```

입력 예시:

- App name: OCR SQLite Starter
- App ID: com.company.ocrsqlite (고유 패키지명, 중복 불가)

패키지명 규칙:
- 소문자
- 도메인 역순 형식 권장 (com.company.appname)

---

## 5. Android 플랫폼 추가

```bash
npm install @capacitor/android
npx cap add android
```

android 폴더가 생성됩니다.

---

## 6. Capacitor 설정 확인

`capacitor.config.ts` 또는 `capacitor.config.json` 확인:

```ts
appId: 'com.company.ocrsqlite',
appName: 'ocr-sqlite-frontend-starter',
webDir: 'dist'
```

주의사항:
- Vite 빌드 결과 폴더가 반드시 dist인지 확인
- 다를 경우 webDir 수정

---

## 7. 빌드 및 동기화

### 1단계: 웹 빌드

```bash
npm run build
```

### 2단계: Android 동기화

```bash
npx cap sync android
```

변경사항 반영 시 항상 sync 실행 필요

---

## 8. Android Studio에서 실행

```bash
npx cap open android
```

실행 절차:

1. Gradle Sync 완료 대기
2. 에뮬레이터 실행 또는 실제 기기 USB 연결
3. Run 버튼 클릭

---

## 9. APK 생성 (테스트용)

Android Studio 메뉴:

Build → Build Bundle(s) / APK(s) → Build APK(s)

생성 위치:

android/app/build/outputs/apk/

테스트 배포 또는 내부 QA용 사용

---

## 10. AAB 생성 (Play Store 배포용)

Android Studio 메뉴:

Build → Generate Signed Bundle / APK

절차:

1. Android App Bundle 선택
2. Keystore 생성 또는 선택
3. Release 빌드 선택
4. 서명 후 AAB 생성

출력 위치:

android/app/build/outputs/bundle/release/

Google Play 배포 시 AAB 사용 권장

---

## 11. 버전 관리

android/app/build.gradle 파일 내:

versionCode 1
versionName "1.0"

업데이트 시:
- versionCode는 반드시 증가
- versionName은 사용자 표시 버전

---

## 12. 권장 설정

### 1) 앱 아이콘 설정
android/app/src/main/res/mipmap 폴더 수정

### 2) 권한 설정
android/app/src/main/AndroidManifest.xml

예:
- 인터넷 권한
- 카메라 권한
- 저장소 권한

### 3) ProGuard / R8 설정
릴리즈 빌드 시 난독화 여부 검토

---

## 13. 자주 발생하는 오류

### Gradle 오류
- File → Sync Project with Gradle Files 재실행

### SDK 오류
- SDK Manager에서 Android API 설치 여부 확인

### 패키지명 변경 오류
- appId
- AndroidManifest.xml
- build.gradle
동기화 여부 확인

---

## 14. 운영 시 권장 절차

1. Git 버전 관리 필수
2. test 스크립트 구성 권장
3. CI/CD 자동 빌드 구성 권장
4. 정기적인 npm audit 수행

---

## 15. 결론

본 절차를 통해 웹 기반 프로젝트를
Android 네이티브 앱 형태로 확장할 수 있습니다.

개발 테스트 → APK  
스토어 배포 → AAB  

Capacitor를 활용하면 기존 웹 코드를 유지하면서
모바일 앱으로 확장이 가능합니다.
