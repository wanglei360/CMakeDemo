# CMakeLists.txt
# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.
#CMakeLists.txt
cmake_minimum_required(VERSION 3.18.1)

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
add_library(
        # 设置so文件名称.
        Hello
        # 设置这个so文件为共享.
        SHARED
        # Provides a relative path to your source file(s).
        JniStrTest.cpp
        BitmapUtil.cpp
)
# Searches for a specified prebuilt library and stores the path as a variable.
# Because CMake includes system libraries in the search path by default
# you only need to specify the name of the public NDK library you want to add.
# CMake verifies that the library exists before completing its build.
find_library( # 设置路径变量的名称.
        log-lib
        # Specifies the name of the NDK library that
        # you want CMake to locate.
        log)

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.
target_link_libraries( # Specifies the target library.
        # 制定目标库.
        Hello
        #JNI层,添加bitmap支持
        jnigraphics
        # Links the target library to the log library
        # included in the NDK.
        ${log-lib})