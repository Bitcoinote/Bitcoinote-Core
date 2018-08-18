Copyright (c) 2012-2017, The CryptoNote developers, The Bytecoin developers, The Forknote developers  
Copyright (c) 2017-2018, The BitcoiNote developers

# BitcoiNote Core

BitcoiNote (BTCN) is a cryptocurrency based on CryptoNote.

**P2P Port:** 28388  
**RPC Port:** 28389

## Build

Currently, build is supported out of the box only on Linux (tested with Ubuntu 16.04) and Windows (64-bit only). Mac OS should theoretically work but is untested.

### Linux

Tested only with Ubuntu 16.04.

Dependencies: GCC 4.7.3 or later, CMake 2.8.6 or later, Boost 1.58.

You may download them from:  
[http://gcc.gnu.org/](http://gcc.gnu.org/)  
[http://www.cmake.org/](http://www.cmake.org/)  
[http://www.boost.org/](http://www.boost.org/)  
[https://www.qt.io/](https://www.qt.io/)  
Alternatively, it may be possible to install them using a package manager.

To build, run the following commands in the project's root directory:

```
mkdir build
cd build
cmake -DPORTABLE=1 ..
make
```

The resulting executables can be found in `build/src` directory which will be created. (For Windows, look in subfolder `Release` or `Debug` respectively.)

### Windows 64bit

Dependencies:
```
libboost 1.58 or greater (Tested with 1.65.1)
cmake 2.8.6 or greater (Tested with 3.10.2)
Microsoft Visual Studio 2013 (Tested with VS2015)
Visual C++ Build Tools v120 (Tested with v140)
```

To build, run the following commands in the project's root directory, but make sure to substitute the Visual Studio version for the one that you use, and to replace the VCTargetsPath with one that works for you:

```
mkdir build
cd build
set PATH="c:\Program Files (x86)\Windows Kits\10\bin\10.0.15063.0\x64";%PATH%
set VCTargetsPath=C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\v140
cmake -G "Visual Studio 14 Win64" -DPORTABLE=1 -DCMAKE_BUILD_TYPE=Release ..
msbuild Bitcoinote.sln /m /p:Configuration=Release
```

In your build folder there should now be a new folder named `Release`, with the binaries.
You still need to copy some library files into that folder:

```
C:\Windows\System32\msvcp140.dll
C:\Windows\System32\msvcrt.dll
C:\WINDOWS\system32\ucrtbase.dll
C:\WINDOWS\system32\vcruntime140.dll
```

To compile the debug version, omit the `/p:Configuration=Release` parameter. Then you need to copy the debug dlls instead of the normal ones. These have the same name, only with a `d` at the end (e.g. `Qt5Cored.dll`), and are in the same location, except for `ucrtbased.dll` which you can find in `C:\Program Files (x86)\Windows Kits\10\bin\x64\ucrt\ucrtbased.dll`.

### macOS

Tested only with macOS High Sierra 10.13.6.

Dependencies: `clang 9.1.0` or later, `CMake 3.5.2` or later, `Boost 1.67` or later and `Qt5` (tested with `Qt 5.10.1`).

* Use [Homebrew](https://brew.sh/) to install `cmake` and `boost`.
* Use [qt.io](https://www.qt.io/) to install QtCreator.

To build, open the `CMakeLists.txt` in QtCreator. Also you can turn on `PORTABLE` flag in the project settings tab.

## Usage Notes

The following files are created:

* `Bitcoinoted`: The main coin daemon.
* `miner`: Stand-alone miner tool (requires daemon).
* `simplewallet`: Command-line wallet tool (if started with `--rpc-bind-port 1234` it will expose a simplified JSON RPC wallet interface).
* `walletd`: Wallet daemon (exposes full Payment Gate Service RPC interface on default port `8070`).
* `connection_tool`: Connection tool.

Start them with the parameter `--help` to get usage information.
