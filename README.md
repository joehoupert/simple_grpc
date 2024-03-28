# gRPC C++ Hello World Example

You can find a complete set of instructions for building gRPC and running the
Hello World app in the [C++ Quick Start][].

[C++ Quick Start]: https://grpc.io/docs/languages/cpp/quickstart

# Real Talk

Want to play around with gRPC?  Want to build that project with Makefiles?  Haiiiiiiiiiiiiii

This repo takes the helloworld cpp example from the gRPC project and the corresponding Makefile and gets it all working together.

# Building

Here's what I did to get gRPC built

```bash
# Put it somewhere
pushd /home

# Clone gRPC
git clone git@github.com:grpc/grpc.git
pushd grpc
git submodule update --init --recursive
popd

# You'll need some things
sudo apt-get update
sudo apt-get install -y cmake build-essential autoconf libtool pkg-config libssl-dev libre2-dev zlib1g-dev

# Put it somewhere
export MY_INSTALL_DIR=/home/.local
mkdir -p $MY_INSTALL_DIR
export PATH="$MY_INSTALL_DIR/bin:$PATH"

# Build gRPC
mkdir -p grpc/cmake/build
pushd grpc/cmake/build
cmake -DgRPC_INSTALL=ON -DgRPC_BUILD_TESTS=OFF -DCMAKE_INSTALL_PREFIX=$MY_INSTALL_DIR ../..
make -j 4
make install
popd
```

Here's what I did to build the helloworld app
```bash
# Put it somewhere
cd /home/simple_grpc

# Clone this repo
git clone git@github.com:joehoupert/simple_grpc.git
pushd simple_grpc
make

```

