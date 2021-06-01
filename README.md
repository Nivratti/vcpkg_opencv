# vcpkg_opencv
Setup opencv using [vcpkg package manager](https://github.com/microsoft/vcpkg)

## Setup vcpkg: Unix
Prerequisites for Linux:

Git
g++ >= 6

First, download and bootstrap vcpkg itself; it can be installed anywhere, but generally we recommend using vcpkg as a submodule for CMake projects.

```sh
$ git clone https://github.com/microsoft/vcpkg
$ ./vcpkg/bootstrap-vcpkg.sh
```

To install the libraries for your project, run:

```sh
$ ./vcpkg/vcpkg install [packages to install]
```

You can also search for the libraries you need with the `search` subcommand:

```sh
$ ./vcpkg/vcpkg search [search term]
```

In order to use vcpkg with CMake, you can use the toolchain file:

```sh
$ cmake -B [build directory] -S . -DCMAKE_TOOLCHAIN_FILE=[path to vcpkg]/scripts/buildsystems/vcpkg.cmake
$ cmake --build [build directory]
```
OR
You can set `CMAKE_TOOLCHAIN_FILE` in CMakeLists.txt.
```sh
cmake_minimum_required(VERSION 3.9)
set( CMAKE_TOOLCHAIN_FILE "[path to vcpkg]/scripts/buildsystems/vcpkg.cmake"  )
```
