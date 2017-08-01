## 1. Introduction
This library is a light version of ZXing barcodescanner library. It supports only QR code scan and takes very less space. It's new UI is specifically made to make it look like QR code scanner.

## 2. Screenshots
iOS 7 (iPhone)

![ScreenShot](https://raw.githubusercontent.com/bhavitsengar/qrcodescanner-lib-android/master/barcodescanner/src/main/res/raw/Screenshot1.jpeg)


### Steps to build a new .aar
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
