
#  Firebase console

Agregar Android app

![[Pasted image 20240829175650.png]]


"com.example.appname"

* Generate shakey

```
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
```

Add autenticacion email and gmail

build.gradle - Android Level

```
buildscript {

repositories {

google()

mavenCentral()

jcenter()

}

  

dependencies {

classpath 'com.android.tools.build:gradle:7.4.2'

classpath 'com.google.gms:google-services:4.4.1'

}

}

allprojects {

repositories {

google()

mavenCentral()

jcenter()

}

}

  

rootProject.buildDir = "../build"

subprojects {

project.buildDir = "${rootProject.buildDir}/${project.name}"

}

subprojects {

project.evaluationDependsOn(":app")

}

  

tasks.register("clean", Delete) {

delete rootProject.buildDir

}
```

build.gradle level App

```
plugins {

id "com.android.application"

id "kotlin-android"

id "dev.flutter.flutter-gradle-plugin"

id 'com.google.gms.google-services'

}

  

def localProperties = new Properties()

def localPropertiesFile = rootProject.file('local.properties')

if (localPropertiesFile.exists()) {

localPropertiesFile.withReader('UTF-8') { reader ->

localProperties.load(reader)

}

}

  

def flutterVersionCode = localProperties.getProperty('flutter.versionCode')

if (flutterVersionCode == null) {

flutterVersionCode = '1'

}

  

def flutterVersionName = localProperties.getProperty('flutter.versionName')

if (flutterVersionName == null) {

flutterVersionName = '1.0'

}

  

android {

namespace = "com.example.vialika"

compileSdk = flutter.compileSdkVersion

ndkVersion = flutter.ndkVersion

  

compileOptions {

sourceCompatibility = JavaVersion.VERSION_1_8

targetCompatibility = JavaVersion.VERSION_1_8

}

  

sourceSets {

main.java.srcDirs += 'src/main/kotlin'

}

defaultConfig {

// TODO: Specify your own unique Application ID (https://developer.android.com/studio/build/application-id.html).

applicationId = "com.example.vialika"

// You can update the following values to match your application needs.

// For more information, see: https://flutter.dev/to/review-gradle-config.

minSdkVersion 26

targetSdkVersion 31

versionCode flutterVersionCode.toInteger()

versionName flutterVersionName

  

multiDexEnabled true

}

  

buildTypes {

release {

// TODO: Add your own signing config for the release build.

// Signing with the debug keys for now, so `flutter run --release` works.

signingConfig = signingConfigs.debug

}

}

}

  

flutter {

source = "../.."

}

  

dependencies {

implementation platform('com.google.firebase:firebase-bom:32.8.0')

implementation "androidx.profileinstaller:profileinstaller:1.3.1"

}
```


Manifest

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android">

  

<uses-permission android:name= "android.permission.ACCESS_FINE_LOCATION" />

<uses-permission android:name= "android.permission.ACCESS_COARSE_LOCATION" />

<uses-permission android:name="android.permission.CAMERA" />

<uses-permission android:name="android.permission.INTERNET" />

<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>

<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>

<uses-permission android:name="android.permission.READ_MEDIA_IMAGES" />

<uses-permission android:name="android.permission.READ_MEDIA_VIDEO" />

<uses-permission android:name="android.permission.READ_MEDIA_AUDIO" />

<uses-permission android:name="android.permission.USE_BIOMETRIC" />

<application

android:label="vialika"

android:name="${applicationName}"

android:icon="@mipmap/ic_launcher">

<activity

android:name=".MainActivity"

android:exported="true"

android:launchMode="singleTop"

android:taskAffinity=""

android:theme="@style/LaunchTheme"

android:configChanges="orientation|keyboardHidden|keyboard|screenSize|smallestScreenSize|locale|layoutDirection|fontScale|screenLayout|density|uiMode"

android:hardwareAccelerated="true"

android:windowSoftInputMode="adjustResize">

<!-- Specifies an Android theme to apply to this Activity as soon as

the Android process has started. This theme is visible to the user

while the Flutter UI initializes. After that, this theme continues

to determine the Window background behind the Flutter UI. -->

<meta-data

android:name="io.flutter.embedding.android.NormalTheme"

android:resource="@style/NormalTheme"

/>

<intent-filter>

<action android:name="android.intent.action.MAIN"/>

<category android:name="android.intent.category.LAUNCHER"/>

</intent-filter>

</activity>

<!-- Don't delete the meta-data below.

This is used by the Flutter tool to generate GeneratedPluginRegistrant.java -->

<meta-data

android:name="flutterEmbedding"

android:value="2" />

</application>

<!-- Required to query activities that can process text, see:

https://developer.android.com/training/package-visibility and

https://developer.android.com/reference/android/content/Intent#ACTION_PROCESS_TEXT.

  

In particular, this is used by the Flutter engine in io.flutter.plugin.text.ProcessTextPlugin. -->

<queries>

<intent>

<action android:name="android.intent.action.PROCESS_TEXT"/>

<data android:mimeType="text/plain"/>

</intent>

</queries>

</manifest>
```

