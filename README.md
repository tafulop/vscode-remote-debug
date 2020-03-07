# Visual Studio Code remote debugging for C++

## Introduction

In this short tutorial, a remote debugging session will be set up with Visual Studio Code via gdb. Please follow these simple steps in order to set up this environment.

For the sake of a simple example, the gdbserver and the gdb (client) will run on the same network - although of course this should work over any network, if the specified port is accessible on the server by the client.

## Prerequisites
* Linux machine (The example was tested on Ubuntu 16.04)

# Setup steps


## Client side

1. The code will be built on the client side. To build it, you may need to install the build tools.
```bash
sudo apt install build-essential
```

2. The next step is to git clone && build the code with debug symbols
```bash
git clone <this repo> ./
g++ -g3 -o hello ./hello_debugger.cpp
```

3. Deploy the application on the server side
Normally you would like to deploy the binary with debug symbols on the server side, so do that with your own deployment method. In this example, the server will be running on the same machine, so a specified path will represent the server.
```bash
mkdir ./server-mock
cp ./hello ./server-mock/
```




## Server side

1. Install gdb server
```bash
sudo apt install gdbserver
```

2. Deploy the application
To get the best result, use a debug build. In this case, I have 
