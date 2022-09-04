steinberg-vst3-boilerplate
==========================
### How to build
1. Build [steinbergmedia/vst3sdk: VST 3 Plug-In SDK](https://github.com/steinbergmedia/vst3sdk) outside of the project first (note that `C:\Windows\System32` is required in `%PATH%`)
    ```cmd
    set PATH=%PATH%;^
    D:\Softwares\cmake-3.23.0-rc1-windows-x86_64\bin;

    cmake.exe -G "Visual Studio 16 2019" -A x64 ^
    -DCMAKE_BUILD_TYPE=Release ^
    -DBUILD_SHARED_LIBS=OFF ^
    -DSMTG_CREATE_PLUGIN_LINK=0 ^
    -DCMAKE_INSTALL_PREFIX="build/vst3sdk-installation" -B./build &&^
    cd build
    cmake --build . && cmake --install .
    pause
    ```
2. Build this project (`local-build.cmd`, `C:\Windows\System32` is also required)

### How to use
1. Copy the folder under `build\VST3\Release\` to `C:\Program Files\Common Files\VST3`
2. Refresh the DAW (rescan vsts)