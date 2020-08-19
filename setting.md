# RN setting

1. git clone

2. ios

   2-1)

   ```bash
   yarn
   cd ios
   pod install
   cd ..
   yarn ios
   ```

3. Android

   3-1)

   - open 안드로이드 스튜디오
   - Configure
   - AVD manager 
   - 초록색 버튼

   3-2)

   run 실패했을때

   - 캐시를 한번 지워준다.

   ```bash
   cd android
   ./gradlew clean 
   ```

   - 포트설정해준다.

     - Command + m

     - Settings

     - Debugging (Debug server host & port for device)

       Localhost:8081