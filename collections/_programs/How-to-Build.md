---
title: How to Build
chapter: 1
layout: default
---
# How to Build

## Getting the Code

To download all of the code of HoT, clone the `hot` repository and its submodules.

```shell
git clone https://github.com/houseoftokens/hot.git --recursive
```

If a repository is cloned without the `--recursive` flag, the submodules can be cloned at a later time:

```bash
git submodule update --init --recursive
```

##  System Requirements

- 7GB RAM free required
- 20GB Disk free required

## Build Options

HoT can be built on several platforms with various paths to building. The majority of users will prefer to use the autobuild script or docker, while more advanced users, or users wishing to deploy a public node may desire manual methods. The build places content in the `hot/build` folder. The executables can be found in subfolders within the `hot/build/programs` folder.

## Autobuild Script

There is an automated build script that can install all dependencies and build HoT.

The script supports the following operating systems.

Amazon Linux 2
CentOS 7
Ubuntu 16.04
Ubuntu 18.04
MacOS 10.14 (Mojave)

Run the build & install script from the `hot` folder.

```bash
cd eos
./scripts/hot_build_install.sh
```

## Manually Build

To manually build, use the following steps to create a `build` folder within your `hot` folder and then perform the build. The steps below assume the `hot` repository was cloned into your home (i.e., `~`) folder. It is also assumes that the necessary dependencies have been installed. 

> ### Dependencies
>
> This project is written primarily in C++14 and uses CMake as its build system. An up-to-date Clang and the latest version of CMake is recommended.
>
> Dependencies:
>
> - Clang 4.0.0
> - CMake 3.5.1
> - Boost 1.66
> - OpenSSL
> - LLVM 4.0
> - [secp256k1-zkp (Cryptonomex branch)](https://github.com/cryptonomex/secp256k1-zkp.git)

```bash
cd ~
mkdir -p ~/hot/build && cd ~/hot/build
```

On Linux platforms, use this `cmake` command:

```shell
cmake -DBINARYEN_BIN=~/binaryen/bin -DWASM_ROOT=~/wasm-compiler/llvm -DOPENSSL_ROOT_DIR=/usr/local/opt/openssl -DOPENSSL_LIBRARIES=/usr/local/opt/openssl/lib -DBUILD_MONGO_DB_PLUGIN=true ..
```

On MacOS, use this `cmake` command:

```shell
cmake -DBINARYEN_BIN=~/binaryen/bin -DWASM_ROOT=/usr/local/wasm -DOPENSSL_ROOT_DIR=/usr/local/opt/openssl -DOPENSSL_LIBRARIES=/usr/local/opt/openssl/lib -DBUILD_MONGO_DB_PLUGIN=true ..
```

Then on all platforms except macOS:

```shell
make -j$( nproc )
```

For macOS run this:

```shell
make -j$(sysctl -n hw.ncpu)
```

Out-of-source builds are also supported. To override clang's default choice in compiler, add these flags to the CMake command:

```
-DCMAKE_CXX_COMPILER=/path/to/c++ -DCMAKE_C_COMPILER=/path/to/cc
```

For a debug build, add `-DCMAKE_BUILD_TYPE=Debug`. Other common build types include `Release` and `RelWithDebInfo`.

###  Make Install

For ease of contract development, content can be installed in the `/usr/local` folder using the `make install` target. This step is run from the `build` folder. Adequate permission is required to install.

