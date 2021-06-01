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

## Setup opencv using vcpkg from source

```sh
$ ./vcpkg/vcpkg search opencv
```

To install the opencv libraries for your project, run:

```sh
$ ./vcpkg/vcpkg install opencv
```

Building opencv from source will take much more time. You can use `export` command once you build opencv first time on your system to export opencv binaries. Exported binaries will be much easier to setup opencv on another system with same os, you just need to unzip exported zip file and link it to to CMakeLists.txt using `DCMAKE_TOOLCHAIN_FILE`.
