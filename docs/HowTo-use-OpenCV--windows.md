# HowTo use OpenCV on windows

If working in C++ follow this.

## HowTo

### Download OpenCV

1. Download and execute [opencv-4.5.5-vc14_vc15.exe](https://opencv.org/releases/).
2. Choose folder location, for example: `C:\libs`
3. Download and unzip [OpenCV-MinGW-Build-OpenCV-4.5.5-x64.zip](https://github.com/huihut/OpenCV-MinGW-Build).
4. Go to unziped folder `\OpenCV-MinGW-Build-OpenCV-4.5.5-x64\x64\` and copy the `mingw` folder.
5. Go to `C:\libs\opencv\build\x64` and paste it.
6. Now open 'Edit the System Enviroment variables' and add:

    ```
    C:\libs\opencv\build\x64\mingw\bin
    ```
    ```
    C:\libs\opencv\build\x64\mingw\lib
    ```
7. Restart to completely update the new enviroment variables.

### Import OpenCV libraries

1. Open a project.

2. If working in VSC, then add `C:\\libs\\opencv/*` to project includePath, or if global as `C:\\libs/*`.
3. Its project CMakeLists.txt file must contain:

    ```cmake
    ...
    find_package(OpenCV REQUIRED)
    include_directories(${OpenCV_INCLUDE_DIRS})
    target_link_libraries(${PROJECT_NAME} ... PRIVATE ${OpenCV_LIBS} ...)
    ...
    ```
4. Also, its application CMakeLists.txt file must contain:
    ```cmake
    target_link_libraries(... PUBLIC ${OpenCV_LIBS} ...)
    ```
5. Now, .h files can include OpenCV headers, for example: `#include "opencv2/opencv.hpp`