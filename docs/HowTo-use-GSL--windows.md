# HowTo use GSL on Windows

GSL is the GNU scientific library for numerical computing, this follows the unofficial port of GNU GSL to Microsoft Windows.

## HowTo

### Download GSL package 

1. Go to GSL for Windows [page](https://gnuwin32.sourceforge.net/packages/gsl.htm) and download the Complete package and Sources setups.

2. Run the Complete package:
    - Press Next

    - Accept the agreement, press Next.
    - Choose the Folder where you want to save the files. In my case, in Windows, I prefer to save every external library in a folder `C:\libs`, so in this case, all GSL libraries will be added to `C:\libs\GnuWin32`, press Next.
    - By default Full Installation is selected and Binaries, Documentation and Developer files are mark, if not, mark them, press Next.
    - Choose whether to have a Start Menu Folder with all shortcuts or not, and if yes then its location, press Next.
    - Press Install, it might not take more than 15 seconds, press Finish.
3. Run the Source setup:
    - Press Next

    - Accept the agreement, press Next.
    - Choose the same folder as before, press Next.
    - By default Full Installation is selected and Sources is mark, if not, mark it, press Next.
    - Choose whether to have a Start Menu Folder with all shortcuts or not, and if yes then its location, press Next.
    - Press Install, it might not take more than 15 seconds, press Finish.

### Import GSL libraries

1. Open a project.
2. If working in VSC, then add `C:\\libs\\GnuWin32/*` to project includePath, or if global as `C:\\libs/*`.
3. Its application CMakeLists.txt file must contain the following lines:

    ```cmake
    ...
    set(GSLSOURCE /path/to/libsfolder/GnuWin32)
    include_directories(${GSLSOURCE})
    target_include_directories(... PUBLIC ${GSLSOURCE}/include ...)
    target_link_libraries(... PUBLIC ${GSLSOURCE}/lib/libgsl.a ...)
    ...
    ```
4. Now, .h files can include GSL headers, for example: `#include "gsl/gsl_wavelet2d.h"`

## References

- [https://gnuwin32.sourceforge.net/install.html](https://gnuwin32.sourceforge.net/install.html)