# LLVM-Cross-Compiler-for-ARM-on-x86
LLVM and Clang
LLVM (Low Level Virtual Machine) is a collection of modular and reusable compiler and toolchain technologies. Clang is a compiler front end for the C, C++, and Objective-C programming languages that works with LLVM. It provides a modern, open-source compiler infrastructure.
## Setup Explanation
### Cloning the LLVM Project:
```
git clone https://github.com/llvm/llvm-project.git
`````
This command clones the LLVM project repository from GitHub to your local machine. The repository includes LLVM, Clang, and related tools.
### Creating Build Directories:
```
mkdir llvm-source
cd llvm-source
`````
You create and navigate into a directory where you'll build LLVM. This keeps your source code and build files organized.
### Configuring the Build:
```
cmake -G "Unix Makefiles" -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/path/to/install ../llvm
`````
CMake is used to configure the build system. The -G "Unix Makefiles" flag tells CMake to generate Makefiles. -DCMAKE_BUILD_TYPE=Release sets the build type to release for optimization. -DCMAKE_INSTALL_PREFIX specifies where to install the compiled binaries.

### Building and Installing:
```
make
sudo make install
`````
### Installing QEMU:
```
sudo apt-get update
sudo apt-get install qemu qemu-user qemu-user-static
`````
QEMU is an open-source emulator and virtualizer. qemu-user and qemu-user-static provide user-mode emulation for running programs compiled for different architectures (e.g., ARM).
### hello.c Explanation
The hello.c file is a simple C program:
```
#include <stdio.h>

int main() {
    printf("Hello RISCV!\n");
    return 0;
}
`````
### Compiling and Running ARM Code:
```
clang --target=arm-linux-gnueabi -o hello_arm hello.c
qemu-arm hello_arm
`````
clang --target=arm-linux-gnueabi compiles hello.c for the ARM architecture. qemu-arm runs the ARM binary on your x86_64 machine using QEMU.

