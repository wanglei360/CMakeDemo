* ```Appearance & Behavior ->System Settings->Android SDK->SDK Tools```->勾选LLDB、NDK、CMake
* ```Project Structure->SDK Location```->选择NDK(无法选择，原因不明)，直接在local.propertes中添加 ```ndk.dir=/Users/leiwu/Documents/sdk/ndk/24.0.8215888```也行 **在没有使用到C语言的时候，只是用CMake，不需要使用NDK**

* 配置CMake
  在```build.gradle ->android ->defaultConfig```中添加以下代码块

    ```
    externalNativeBuild{
        cmake{
                // 指定编译架构
                abiFilters 'arm64-v8a','armeabi-v7a','x86','x86_64'
                cppFlags ""
            }
    }
    ```

  ```build.gradle ->android ```->添加以下代码块，指定CMakeLists.txt路径

    ```
    externalNativeBuild{
        cmake{
            // 在该文件种设置所要编写的c源码位置，以及编译后so文件的名字
            //path 'CMakeLists.txt'
            path 'src/main/cpp/CMakeLists.txt'
            }
    }
    ```

点击Sync Now，会在当前module下生成.cxx文件夹












