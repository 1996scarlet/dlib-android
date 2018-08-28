# dlib-android

[![Build Status](https://travis-ci.org/tzutalin/dlib-android.png)](https://travis-ci.org/tzutalin/dlib-android)

### Purpose

* Grab the source:
	
	`$ git clone --recursive https://github.com/tzutalin/dlib-android.git`
	    
* NDK Environment: Export ANDROID_NDK_HOME in ~/.bashrc

		`$ sudo gedit ~/.bashrc`
		`export ANDROID_NDK_HOME=/home/humanmotion/Android/Sdk/ndk-bundle`
		`source ~/.bashrc`
     
* Clone dlib-android-app：

		`$ cd dlib-android/androidstudio-examples`
		`$ git clone https://github.com/tzutalin/dlib-android-app.git`
     
* OpenCV-Android-SDK: 

		`$ cd dlib-android/third_party`
		`$ unzip opencv-3.4.1-android-sdk.zip`
		`$ cp cp -ri OpenCV-android-sdk/sdk/native/* opencv/`

* Get others:
	
	`$ ./envsetup`

### Prerequisites
* Download Android-NDK from [Android website](https://developer.android.com/ndk/downloads/index.html).

	 After downloading, go to the directory to which you downloaded the package to extract it

	 Export ANDROID_NDK_HOME in ~/.bashrc
     `$ vim ~/.bashrc`

	`export ANDROID_NDK_HOME=[NDK_PATH]/android-ndk-[version]`

    `export PATH=$PATH:$ANDROID_NDK_HOME`

* Install Android Debug Bride (ADB). You can download it via [Android SDK Manager](https://developer.android.com/sdk/installing/index.html) or $ sudo apt-get install android-tools-adb

* Prepare an Android device for test

### Build JNI code and shared library for Android application
* You can change the compiler architecture in dlib-android/jni/Application.mk

* The way to build the shared library for Android application

```sh
    $ cd [dlib-android]
    $ python build.py
```

Alternative way to build native code and copy to the Android Studio's project manually:
```sh
    $ cd [dlib-android]
    $ ndk-build -j 2
    $ cp -r libs/* androidstudio-examples/dlib-android-app/dlib/src/main/jniLibs
```

### Folder structure

```
├── data                    # Test data or the models for detection and landmarks
├── dlib                    # Source files of dlib. It is a submodule
├── jni                     # Source files of JNI codes and their make files
├── androidstudio-examples  # Android Studio's projects use the shared library built by this repo
├── tools                   # Tools and utilities
├── third_party             # Like OpenCV and [miniglog](https://github.com/tzutalin/miniglog)
├── CMakeLists.txt          # Use CMake to build instead of using Android.mk
├── LICENSE
└── README.md
```

### Do you want to contribute
 * If you have any improvement or you've found any bug, send a pull request with the code.
 * Give me a star on this repository
 * <a href='https://ko-fi.com/A4263TV2' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi1.png?v=0' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>
