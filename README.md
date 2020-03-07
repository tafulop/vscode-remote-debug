# Visual Studio Code remote debugging for C++

## Introduction

In this short tutorial, a remote debugging session will be set up with Visual Studio Code via gdb. Please follow these simple steps in order to set up this environment.

For the sake of a simple example, the gdbserver and the gdb (client) will run on the same network - although of course this should work over any network, if the specified port is accessible on the server by the client.

## Prerequisites
* Linux (The example was tested on Ubuntu 16.04)
* VSCode installed on the client (version 1.42.1 was used in this tutorial)

# Setup steps

## Client side

0. Install required tools (optional depending on your current installation)
```bash
sudo apt install build-essential gdb
```

1. The code will be built on the client side. To build it, you may need to install the build tools.
```bash
sudo apt install build-essential
```

2. The next step is to git clone && build the code with debug symbols
```bash
git clone <this repo> ./
cd vscode-remote-debug
mkdir ./hello-debug/build
cd ./hello-debug/build
g++ -g3 -o ./hello ../hello.cpp
```

3. Deploy the application on the server side
Normally you would like to deploy the binary with debug symbols on the server side, so do that with your own deployment method. In this example, the server will be running on the same machine, so a specified path will represent the server.
```bash
mkdir ../../server-mock
cp hello ../../server-mock/
```

## Server side

1. Install gdb server
```bash
sudo apt install gdbserver
```

# Running the example

## Server side

1. Start gdbserver
As mentioned before, in this example the same host will be used for running the gdbserver and the gdb client.
```bash
cd ../../server-mock
gdbserver localhost:2159 ./hello
```

## Client side

1. Start Visual Studio Code

You just need to open the folder "vs-project" since the example is already set up.

2. Start debugging

Just click on the Debug/Start debug button or hit F5 to start debugging.

In the end, it should look similar to this:

![alt text](https://github.com/tafulop/vscode-remote-debug/blob/master/screenshot/debug_running.png?raw=true)



3. Find all the bugs and enjoy your day! :)
