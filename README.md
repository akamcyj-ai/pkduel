# 승부차기 대결 — 안드로이드 앱 프로젝트

아들과 각자의 안드로이드 폰으로 연결해서 하는 승부차기 게임입니다.
게임 화면은 `app/src/main/assets/index.html`, 앱 껍데기는 `MainActivity.java`(WebView)입니다.

## APK 만드는 방법 ① — 설치 없이 GitHub에서 (추천)
1. github.com 로그인 → 오른쪽 위 **+ → New repository** → 이름 `pkduel` → Create
2. **uploading an existing file** 클릭 → 압축 푼 `PKDuel` 폴더 **안의 내용 전체**를 끌어다 놓기 → Commit
   - `.github` 폴더(숨김 폴더)가 안 올라갔다면: **Add file → Create new file** → 파일 이름에
     `.github/workflows/build-apk.yml` 입력 → 이 프로젝트의 같은 파일 내용을 붙여넣고 Commit
3. 위쪽 **Actions** 탭 → `Build APK` 실행이 끝날 때까지 3~5분 대기 (초록 체크)
4. 실행 항목을 눌러 아래 **Artifacts**에서 `승부차기대결-apk` 다운로드 → 압축 풀면 `app-debug.apk`

## APK 만드는 방법 ② — Android Studio
1. Android Studio 설치 → **Open** → `PKDuel` 폴더 선택 → Gradle 동기화가 끝날 때까지 대기
2. 메뉴 **Build → Build App Bundle(s) / APK(s) → Build APK(s)**
3. 완료 알림의 **locate** → `app/build/outputs/apk/debug/app-debug.apk`

## 폰에 설치
1. APK 파일을 두 폰으로 보내기 (카카오톡 '나에게 보내기', 구글 드라이브 등)
2. 폰에서 파일 열기 → "출처를 알 수 없는 앱 설치" 허용 → 설치
   (Play 프로텍트 경고가 나오면 '무시하고 설치' — 직접 만든 앱이라 나오는 경고입니다)

## 온라인 대결
- 두 폰 모두 인터넷(와이파이 또는 데이터) 필요. 서로 다른 장소에 있어도 됩니다.
- 한 폰에서 **방 만들기** → 4자리 번호를 다른 폰에서 **방 번호로 참가**에 입력.
- 연결은 WebRTC(PeerJS)로 폰끼리 직접 이어지고, 서로를 찾을 때만 PeerJS 무료 공용 서버를 씁니다.
- 인터넷이 없으면 **한 폰으로 둘이 하기**는 그대로 됩니다.
