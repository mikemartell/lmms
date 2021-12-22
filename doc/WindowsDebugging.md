 
X64WindowsBuilds
# Building LMMS for Windows
 
## Install Visual Studio
 
* Desktop Development with C++
    *  MSCV
    * Windows 10 SDK
    * JIT
    * C++ profiling
    * C++ Cmake tools
    * C++ ATL
    * C++ Address Sanitizer
 
## Install QT
https://www.qt.io/download-qt-installer
 
Follow the installer and create a free account if you do not have one already. When you get to the 'Select Components' stage, make sure the following are selected:
 
* Latest version of QT
    * MSVC 2019 32-bit
    * MSVC 2019 64-bit
* Developer and Designer Tools
    * Qt Creator 4.13.2 CDB Debugger Support (optional). Visual Studio also is a great debugger.
    * Debugging Tools for Windows
 
## Clone vcpkg
https://github.com/Microsoft/vcpkg
 
## Install vcpkg
Run the `bootstrap-vcpkg.bat` file in the vcpkg source code.
 
## Use vcpkg to install dependencies
In the vcpkg source code folder, open a terminal and run the following command
 
```
.\vcpkg install fftw3 libsamplerate libsndfile lilv lv2 sdl2 --triplet x64-windows
```
 
## Clone LMMS
https://github.com/LMMS/lmms
 
## Build and Debug LMMS
1. Open "x64 Native Tools Command Prompt"
1. cd \<root of your lmms repo\>
3. mkdir build
4. cd build
1. cmake .. -Tv142,host=x64 -DCMAKE_PREFIX_PATH=C:/Qt5/5.15.2/msvc2019_64 -DCMAKE_TOOLCHAIN_FILE=C:/users/michael/Source/Repos/vcpkg/scripts/buildsystems/vcpkg.cmake
   * Note: Replace paths with your actual paths.
1. cmake --build . -- /m
   * Alternatively, open the lmms.sln file and build in Visual Studio.
1. Start Debugging! (set any breakpoints and hit F5)
 
## Install optional dependencies
* In `CMake Settings` tick the `Show advanced varibles` checkbox.
* Install Git
    * https://git-scm.com/downloads
    * Run the installer.
    * In `CMake Settings` set the `GIT_EXECUTABLE` variable to the location of your `git.exe`
        * This is normally found in someplace like `C:\Program Files\Git\cmd\git.exe`
* Install PkgConfig
    * https://download.gnome.org/binaries/win32/dependencies/pkg-config_0.26-1_win32.zip
    * Extract the zip files to a permanent place.
    * In `CMake Settings` set the `PKG_CONFIG_EXECUTABLE` variable to the new location of your `pkg-config.  exe`
* `pkg-config.exe` is found inside the `bin` folder in the download.
* Install Doxygen
* https://www.doxygen.nl/download.html
* In `CMake Settings` set the `DOXYGEN_EXECUTABLE` variable to the location of your `doxygen.exe`
* This is normally found in someplace like `C:\Program Files\doxygen\bin\doxygen.exe`
 
Video:
https://www.youtube.com/watch?v=UIKGc4ezVGk