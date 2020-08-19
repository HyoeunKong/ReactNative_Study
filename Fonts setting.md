# React Native Fonts 적용

💁‍♀️💡 가장 먼저 해야할 일은 폰트 다운 받기!



### IOS

1. 다운로드 받은 폰트 파일을 ios/Fonts 폴더를 만들고 그 안에 복사한다.

   ![ios_font1](https://raw.githubusercontent.com/HyoeunKong/ReactNative_Study/master/image/ios_font1.png)



2. 폰트 파일을 복사한 후 ios/project_name.xcodeproj 또는 ios/project_name.xcworkspace 를 실행 하여 xcode 를 실행한다.

   

3. 왼쪽 상단에 프로젝트 명을 우클릭하여 Add Files to "project_name"...을 선택한다.

   ![ios_font2](https://raw.githubusercontent.com/HyoeunKong/ReactNative_Study/master/image/ios_font2.png)

4. 위와 같이 파일 선택화면이 나오면 우리가 추가한 ios/Fonts 폴더를 선택하고 Create folder references를 선택한 후, Add를 눌러 폴더를 추가한다.

   ![ios_font3](https://raw.githubusercontent.com/HyoeunKong/ReactNative_Study/master/image/ios_font3.png)

5. Info.plistdp Fonts provided by application을 추가하고 폰트 파일을 추가 한다.

   🚫Fonts 를 bolierplate 폴더 안에 집어 넣어야 한다..(왜인지는 잘모르겠음)

   ![ios_font4](https://raw.githubusercontent.com/HyoeunKong/ReactNative_Study/master/image/ios_font4.png)

5. pod install 한번 해주고 다시 빌드한다. 



### Android

🙋‍♀️ Android 는 ios 보다 훨씬 간단하다.

android/app/src/main/assets/fonts 폴더를 만들고 다운받은 폰트를 넣어주면 끝

![ios_font5](https://raw.githubusercontent.com/HyoeunKong/ReactNative_Study/master/image/ios_font5.png)
