[![](https://jitpack.io/v/ibitcy/eo-mobile-openssl-static.svg)](https://jitpack.io/#ibitcy/eo-mobile-openssl-static)

## OpenSSL static library + prefab

Easy to use solution to bake fresh version of OpenSLL into your NDK Library

## Why we did it:

Using [Google's Prefabbed OpenSLL library ](https://mvnrepository.com/artifact/com.android.ndk.thirdparty/openssl) you'll face a problem with libssl.so and libcrypto.so on devices with Android 5

In this cases the one and only way to have latest version of OpenSSL in your app is merge it into your library

But you can have the best of both worlds: easy to implement prefab dependency + static .a libraries that will guarantee that your code will work on any version of Android as you expect

## How to

1. Add dependency to your build.gradle:
```gradle
dependencies {
    ...
    implementation 'com.github.ibitcy:eo-mobile-openssl-static:1.1.1l'
    ...
}
```
2. Add this code pieces to your CMakeLists.txt:
```cmake
find_package(openssl REQUIRED CONFIG)
...
get_target_property(OPENSSL_INCLUDE_DIR openssl::ssl INTERFACE_INCLUDE_DIRECTORIES)
...
set_target_properties(openssl::crypto PROPERTIES IMPORTED_LOCATION ${OPENSSL_INCLUDE_DIR}/../../../../jni/include/lib/${CMAKE_ANDROID_ARCH_ABI}/libcrypto.a)
set_target_properties(openssl::ssl PROPERTIES IMPORTED_LOCATION ${OPENSSL_INCLUDE_DIR}/../../../../jni/include/lib/${CMAKE_ANDROID_ARCH_ABI}/libssl.a)
...
target_link_libraries(
        your_library_name
        ...
        openssl::ssl
        openssl::crypto
        ...
)
```
3. Build! 🎉🎉🎉
