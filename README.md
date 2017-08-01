## 1. Introduction
This library is a light version of ZXing barcodescanner library. It supports only QR code scan and takes very less space. It's new UI is specifically made to make it look like a QR code scanner.

## 2. Screenshots

![ScreenShot](https://raw.githubusercontent.com/bhavitsengar/qrcodescanner-lib-android/master/barcodescanner/src/main/res/raw/Screenshot1.jpeg)
![ScreenShot](https://raw.githubusercontent.com/bhavitsengar/qrcodescanner-lib-android/master/barcodescanner/src/main/res/raw/Screenshot2.jpeg)

#### 3. Usage

Add an entry of CaptureActivity in AndroidManifest.xml : 
```js
<activity android:name=".CaptureActivity"
              android:screenOrientation="sensorLandscape"
              android:clearTaskOnLaunch="true"
              android:stateNotNeeded="true"
              android:theme="@style/CaptureTheme"
              android:windowSoftInputMode="stateAlwaysHidden">
      <intent-filter>
        <action android:name="com.google.zxing.client.android.SCAN"/>
        <category android:name="android.intent.category.DEFAULT"/>
      </intent-filter>
</activity>      
```

Call the CaptureActivity.java like below to start scan :
```js
Intent intentScan = new Intent(MainActivity.this, CaptureActivity.class);
   intentScan.setAction("com.google.zxing.client.android.SCAN");
   intentScan.addCategory(Intent.CATEGORY_DEFAULT);
                
   intentScan.putExtra("SCAN_CAMERA_ID", 1); // Which camera would you prefer? 1 is for front-camera and 0 is for rear-camera.
   intentScan.putExtra("SHOW_FLIP_CAMERA_BUTTON", true); // true or false, whether you want to show flip camera button or not.
   intentScan.putExtra("SHOW_TORCH_BUTTON", true); // true or false, whether you want to show torch button or not.
   intentScan.putExtra("TORCH_ON", true); // true or false, whether you want flash torch ON by default.
   intentScan.putExtra("BEEP_ON_SCAN", true); //true or false, whether you want a beep sound on successful scan.
   intentScan.putExtra("PROMPT_MESSAGE", "Scan QR Code to pay"); // a text you want to show to user on scan screen.
   
   startActivityForResult(intentScan, 1);
```
And handle the result in onActivityResult() :

```js
@Override
public void onActivityResult(int requestCode, int resultCode, Intent intent) {
   if (requestCode == 1) {
      if (resultCode == Activity.RESULT_OK) {
         String resultString = intent.getStringExtra("SCAN_RESULT");
      } else if (resultCode == Activity.RESULT_CANCELED) {
         // User cancelled the scan by pressing back button.
      }
   }
 }
```

### 4. Steps to build a new .aar
 * Clone this repo
 * Open it in Android Studio
 * Update any source files as needed (current version is: https://github.com/zxing/zxing/releases/tag/BS-4.7.6):
   - Copy all files from `core`
   - From the `android` folder grab the src/.../android folder and paste that to the appropriate package
   - Same for `android-core`
   - Note that R.java is generated when building and is supposed to be in build/generated/source/r/debug/barcodescanner/xservices/nl/barcodescanner/R
   - Re-add the 'flip camera' feature and the 'portrait scan' feature I added before!
   - Make sure no `app_name` tag is active in the `res/values*/string.xml` files
 * (Finder/Explorer): Clean barcodescanner > build > outputs
 * Open the Gradle toolwindow
 * Run barcodescanner > Tasks > other > build
 * The (release) .aar will be generated in barcodescanner > build > outputs
 * Commit and push any changes made!
 
 ## Licence ##


Copyright (C) 2017 Bhavit Singh Sengar

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0
    
Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
