# React Native Splash 

Splash -> animation 적용한 splash component 

### react-native-bootsplash 

- 이미지스플래시만 사용가능
- 애니매이션 넣고싶으면 bootsplash hide 하고 애니매이션 적용한 별도의 스플래시 컴포넌트로 이동시켜야함



## IOS / Android 공통

#### 1. 라이브러리 설치

```bash
npm install --save react-native-bootsplash
or
yarn add react-native-bootsplash
```



#### 2. SetUp

```bash
npx generate-bootsplash
or
yarn generate-bootsplash

ios 는 pod install
```

![splash1](https://raw.githubusercontent.com/HyoeunKong/ReactNative_Study/master/image/splash1.png)

- The path to the root of your React Native project : 프로젝트 최상위 경로 
- The path to your static assets directory: 생성된 splash 배경 이미지 들어갈 폴더?
- Your original icon file : splash 배경으로 쓸 이미지 경로
- The bootsplash background color (in hexadeciaml) : splash 배경 색
- The desired icon width (in dp - we recommend approximately ~100) : 배경이미지 width 통 이미지로 할 경우 300, 로고(작은 이미지)일경우 100!
- Are you sure ? y 해주면 됨





## IOS

#### 1. AppDelegate.m file 수정

ios/<MyProjectName>/AppDelegate.m 

```javascript
#import "AppDelegate.h"

#import <React/RCTBridge.h>
#import <React/RCTBundleURLProvider.h>
#import <React/RCTRootView.h>

#import "RNBootSplash.h" // <- add the header import ()

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
  // …
  rootViewController.view = rootView;
  self.window.rootViewController = rootViewController;
  [self.window makeKeyAndVisible];

  [RNBootSplash initWithStoryboard:@"BootSplash" rootView:rootView]; // <- initialization using the storyboard file name (여기)

  return YES;
}
```



#### 2. BootSplash.storyboard 생성

ios/<myProjectName>/BootSplash.storyboard 생성된것을 확인할 수 있음

xCode로 이동 후 MyProjectName 폴더에 BootSplash.storyboard를 넣어준다! 저장후 다시 빌드하면 스플래시가 적용된것을 확인 할 수 있음

### ![splash2](https://raw.githubusercontent.com/HyoeunKong/ReactNative_Study/master/image/splash2.png)



## Android

#### 1. android/app/src/main/java/com/yourprojectname/MainActivity.java  파일 수정

```javascript
import android.os.Bundle; // <- add this necessary import

import com.facebook.react.ReactActivity;
import com.zoontek.rnbootsplash.RNBootSplash; // <- add this necessary import

public class MainActivity extends ReactActivity {

  // …

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    RNBootSplash.init(R.drawable.bootsplash, MainActivity.this); // <- display the generated bootsplash.xml drawable over our MainActivity
  }
```



#### 2. android/app/src/main/res/values/styles.xml  파일 수정

```javascript
<resources>

  <!-- Base application theme -->
  <style name="AppTheme" parent="Theme.AppCompat.Light.NoActionBar">
    <!-- Your base theme customization -->
  </style>

  <!-- Add the following lines -->
  <!-- BootTheme should inherit from AppTheme -->
  <style name="BootTheme" parent="AppTheme">
    <!-- set the generated bootsplash.xml drawable as activity background -->
    <item name="android:background">@drawable/bootsplash</item>
  </style>

</resources>
```



### 3. android/app/src/main/AndroidManifest.xml 파일 수정

``` javascript
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
  package="com.rnbootsplashexample">

  <!-- … -->

  <application
    android:name=".MainApplication"
    android:label="@string/app_name"
    android:icon="@mipmap/ic_launcher"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:allowBackup="false"
    android:theme="@style/AppTheme">

    <!-- set android:launchMode="singleTask", set android:exported="true" -->
    <activity
      android:name=".MainActivity"
      android:label="@string/app_name"
      android:configChanges="keyboard|keyboardHidden|orientation|screenSize|uiMode"
      android:launchMode="singleTask"
      android:windowSoftInputMode="adjustResize"
      android:exported="true">
      <!-- ⚠️ remove the intent-filter from MainActivity -->
    </activity>

    <!-- add the following lines (use the theme you created at step 3) -->
    <activity
      android:name="com.zoontek.rnbootsplash.RNBootSplashActivity"
      android:theme="@style/BootTheme"
      android:launchMode="singleTask">
      <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
      </intent-filter>
    </activity>

    <!-- … -->

  </application>

</manifest>
```



> 그리고 Launch Screen 은 삭제 하면됨 (code, xCode 둘다.)

