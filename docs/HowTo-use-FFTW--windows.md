# HowTo use FFTW on Windows

## Requirements

- Visual Studio 2015 or later.

## HowTo

### Download FFTW

1. Download [fftw-3.3.5-dll64.zip](https://www.fftw.org/install/windows.html).

2. Unzip and save it on your prefereable location, for example: `C:\libs\`
3. Open Developer Command Prompt for VS.
4. Go to unzip folder and type: `lib /machine:x64 /def:libfftw3l-3.def`
5. `libfftw3l-3.exp` and `libfftw3l-3.lib` files will be built.

### Import FFTW libraries

1. Open a project.
2. If working in VSC, then add `C:\\libs\\fftw-3.3.5-dll64/*` to project includePath, or if global as `C:\\libs/*`.
3. Its application CMakeLists.txt file must contain the following lines:

    ```cmake
    ...
    set(FFTWSOURCE /path/to/libsfolder/fftw-3.3.5-dll64)
    include_directories(${FFTWSOURCE})
    target_include_directories(... PUBLIC ${FFTWSOURCE} ...)
    target_link_libraries(... PUBLIC ${FFTWSOURCE}/libfftw3l-3.lib ...)
    ...
    ```
4. Now, .h files can include FFTW headers, for example: `#include "fftw3.h"`.

## References
- [https://www.fftw.org/install/windows.html](https://www.fftw.org/install/windows.html)
- If working in VS, check [here](https://stackoverflow.com/a/39676354).

