⚠️ This repo is obsolete.  It was used in Couchbase Lite Android / Java 1.x.

Java wrapper around [CBForest](https://github.com/couchbaselabs/cbforest).  Includes SWIG generated java wrappers for CBForest.


## Quick Start

```
$ git clone <repo>
$ cd couchbase-lite-java-forestdb
$ git submodule update --init --recursive
```
#### Prerequisites
* 1. Install [SWIG](http://www.swig.org/)  -- Optional: This is required if you want to generate JNI interface files (C/C++/Java) from SWIG interface file.

If you are using Mac OSX
```
$ brew install swig
```

* 2. Install [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) version r10c

Note: Please add ANDROID SDK and NDK home directories in the envronment PATH
```
export ANDROID_HOME=<Android SDK home directory>
export PATH=$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools:$PATH

#export ANDROID_NDK_HOME=<NDK home directory>
#export PATH=$ANDROID_NDK_HOME:$PATH
```

### Build by Gradle

#### How to generate the AAR file for Android
```
$ ./gradlew -Pspec=android  assemble
$ cd build/outputs/aar
```
#### Run UnitTest for Android
```
$ ./gradlew  -Pspec=android connectedAndroidTest --debug
```
#### How to generate the Jar file for Java Desktop
```
$ ./gradlew -Pspec=java assemble
$ cd build/libs
```

### Build cbforest by make for Android platform

#### Generate JNI java and native (C/C++) binding codes by SWIG
```
$ make swig
```
#### Compile JNI native (C/C++) codes by Android NDK
Note: Update Makefile to specify your NDK build command path
```
$ make ndk-build
```
#### Compile JNI java files and make jar file
```
$ make jar
```
#### Outcome 
* cbforest.jar
* libs/[platform]/libcbforest.so

## NOTES
### Build for Linux
* Needs to install clang: `sudo apt-get install clang` for Ubuntu
* Unable to cross-compile x86 build on 64bit machine. `clang` does not work with `gcc-multilib` and `g++-multilib`. We might needs to switch to GCC, but it requires CBForest code changes. 


