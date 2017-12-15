Copyright (c) 2012-2017, The CryptoNote developers, The Bytecoin developers, The Forknote developers  
Copyright (c) 2017, The Bitcoinote developers

# Bitcoinote Core

Bitcoinote (BTCN) is a cryptocurrency based on CryptoNote.

**P2P Port:** 28388  
**RPC Port:** 28389

## Build

Currently, build is supported out of the box only on Linux. Tested with Ubuntu 16.04.

Dependencies: GCC 4.7.3 or later, CMake 2.8.6 or later, and Boost 1.55.

You may download them from:  
[http://gcc.gnu.org/](http://gcc.gnu.org/)  
[http://www.cmake.org/](http://www.cmake.org/)  
[http://www.boost.org/](http://www.boost.org/)  
Alternatively, it may be possible to install them using a package manager.

To build, change to the directory where this file is located, and run `make`. The resulting executables can be found in `build/release/src` directory which will be created.

The following files are created:

* `Bitcoinoted`: The main coin daemon.
* `miner`: Stand-alone miner tool (requires daemon).
* `simplewallet`: Command-line wallet tool (requires `walletd` in same directory).
* `walletd`: Wallet daemon required for `simplewallet`.

Start them with the parameter `--help` to get usage information.
