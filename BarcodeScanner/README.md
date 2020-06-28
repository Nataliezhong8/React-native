#### Reference: https://www.jianshu.com/p/2cef1baf9a6f

#### Introduction: This is my running steps to implement barcode scanning using react-native (using windows10)

### 1. Create a project
1.1 Open cmd and create a project in a specific directory
```
react-native init BarcodeScanner
```
1.2 Go into your project directory and download the reactive-native-camera library
```
npm install react-native-camera@https://github.com/lwansbrough/react-native-camera.git --save
```
1.3 Link it to our scanner application.
```
react-native link react-native-camera
```

### 2. Android Setup
2.1 In the file /android/app/src/main/java/[...]/MainApplication.java

(1)add a dependency
```
import com.lwansbrough.RCTCamera.RCTCameraPackage;
```
(2) In getPackages() add
```
package.add(new RCTCameraPackage()); #??? MainReactPackage()需要加进去嘛？
```
2.2 In the file android/settings.gradle, add:
```
include ':react-native-camera'
project(':react-native-camera').projectDir = new File(rootProject.projectDir,   '../node_modules/react-native-camera/android')
```
2.3 In the file android/app/build.gradle, 
add in dependencies{}
```
implementation project(':react-native-camera'） 
```
(View differences between compile, implementation and api https://blog.csdn.net/richardlovemyfamily/article/details/81233848)

2.4 In the file android/app/src/main/AndroidManifest.xml, add the corresponding permissions:
```
    <uses-permission android:name="android.permission.CAMERA" /> <!--Required to access the camera device-->
    <uses-permission android:name="android.permission.VIBRATE" /> <!--Allows access to the vibrator.-->
    <uses-feature android:name="android.hardware.camera" android:required="false" />
    <uses-feature android:name="android.hardware.camera.front" android:required="false" />
```

#### Note: The first three steps of Android configuration will be automatically added, but if not, follow the above steps to add manually!
