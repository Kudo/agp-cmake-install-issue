Reproducible example for auto install cmake from AGP
====================================================

The example is based on [ndk-samples/hello-jni](https://github.com/android/ndk-samples/tree/7f6936ea044ee29c36b5c3ebd62bb3a64e1e6014/hello-jni). Check [commit history](https://github.com/Kudo/agp-cmake-install-issue/commits/main) for detailed changes.

## Test Steps

1. `sdkmanager --uninstall 'cmake;3.10.2.4988404' && sdkmanager --uninstall 'cmake;3.18.1' && sdkmanager --uninstall 'cmake;3.22.1'`
2. `./gradlew :app:assembleDebug --no-daemon` and check whether cmake can be automatically installed.
3. Update the [test combinations](https://github.com/Kudo/agp-cmake-install-issue/blob/f4465b6f21737db51faaeb6c53fb4f65d6c2fbd4/build.gradle#L6-L19) and start from step.1 until looping over all test cases.

# Result

|              | AGP 7.0 | AGP 7.1 | AGP 7.2 |
| :----------: | :-----: | :-----: | :-----: |
| CMake 3.10.2 |   ✅    |   ❌    |   ❌    |
| CMake 3.18.1 |   ❌    |   ✅    |   ✅    |
| CMake 3.22.1 |   ❌    |   ❌    |   ❌    |
