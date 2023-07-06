# HowTo use GSL on Windows

GSL is the GNU scientific library for numerical computing, this follows the unofficial port of GNU GSL to Microsoft Windows.

## HowTo

### Download GSL 

1. Go to AMPL/GSL [page](https://github.com/ampl/gsl) and clone the repository. For now we will avoid the optional inclusion of the AMPL GSL bindings

2. Go to the gsl cloned and open a terminal there.
3. If working with MinGW, run the following lines:

    ```console
    $ mkdir build
    $ cd build
    $ cmake .. -G"MinGW Makefiles" -DNO_AMPL_BINDINGS=1
    $ MinGW32-make
    ```
4. Now you can rename and move your `\build` folder wherever you want, for example: `C:\\libs\gsl-gnu`

### Import GSL libraries

1. Open a project.
2. If working in VSC, then add `C:\\libs\\gsl-gnu/*` to project includePath, or if global as `C:\\libs/*`.
3. Its application CMakeLists.txt file must contain the following lines:

    ```cmake
    ...
    set(GSL_DIR "C:/libs/gsl-gnu")
    include_directories(${GSL_DIR})
    target_link_libraries(${PROJECT_NAME} PUBLIC ${GSL_DIR}/libgsl.a ${GSL_DIR}/libgslcblas.a)
    ...
    ```
4. Now, .h files can include GSL headers, for example: `#include "gsl/gsl_wavelet2d.h"`

## References

- [https://github.com/ampl/gsl](https://github.com/ampl/gsl)