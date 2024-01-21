This is a fork of [https://github.com/andalevor/sedaman](https://github.com/andalevor/sedaman) and the reason for it is to make it compatible with Windows and MSVC.

# Prerequisites for building on Windows
- Visual Studio with C++ desktop development tools. Make sure that the compiler supports the C++20 standard (you probably don't have to worry about the C++ standard if you are installing the most recent version).
- CMake 3.4 or higher.
- Python 3.6 or higher. But make sure that the python version you're building with matches the version you're building for; for example, if you need the library to run on Python 3.8, you'll have to build it with Python 3.8.

# Building
1. Clone the repository with the --recurse-submodules option.
```
git clone --recurse-submodules https://github.com/andalevor/sedaman
```
2. Generate the visual studio solution.
```
cd sedaman
cmake -DCMAKE_BUILD_TYPE=Release -B .\build
```
3. Navigate to the build directory, open the visual studio solution and build the target `pysedaman`.
4. Import the library.
```
cd build\Release
python
>>> import pysedaman
```

# Troubleshooting
- If CMake failed to generate the visual studio solution or importing the library in python failed, try this first:
    - Sometimes CMake fails to locate the python executable, python include directory or python .lib file. So, explicitly telling CMake where those are might help.
    - We can do that by setting the values for the following variables: `PYTHON_EXECUTABLE`, `PYTHON_INCLUDE_DIR` and `PYTHON_LIBRARY`. Both the python executable and include directory are relatively easy to find, unlike the python library which is a bit tricky sometimes, but usually it resides under `<path-to-python-installation>\libs\`.
    ```
    cmake -DCMAKE_BUILD_TYPE=Release -DPYTHON_EXECUTABLE="<path-to-python-installation>\python.exe" -DPYTHON_INCLUDE_DIR="<path-to-python-installation>\include" -DPYTHON_LIBRARY="<path-to-python-installation>\libs\python3x.lib" -B .\build
    ```
