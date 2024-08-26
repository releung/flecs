
- toolchain.cmake

```cmake
# toolchain.cmake

# 指定目标系统的名称
set(CMAKE_SYSTEM_NAME Linux)
set(CMAKE_SYSTEM_PROCESSOR arm)

# 指定交叉编译器的路径
set(CMAKE_C_COMPILER /home/elliot/wp/006/pndcode/MediaSDK/host-tools/gcc/arm-cvitek-linux-uclibcgnueabihf/bin/arm-linux-gcc)
set(CMAKE_CXX_COMPILER /home/elliot/wp/006/pndcode/MediaSDK/host-tools/gcc/arm-cvitek-linux-uclibcgnueabihf/bin/arm-linux-g++)

# 指定目标系统的根目录 (可选)
set(CMAKE_SYSROOT /home/elliot/wp/006/pndcode/MediaSDK/host-tools/gcc/gcc-linaro-6.3.1-2017.05-x86_64_arm-linux-gnueabihf/arm-linux-gnueabihf/libc)

# 指定目标系统的头文件和库路径 (如果需要)
# set(CMAKE_FIND_ROOT_PATH /path/to/your/sysroot)

# 使 CMake 优先使用目标系统路径而非主机系统路径
set(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)
```

- build-arm.sh

```bash
#!/bin/bash

mkdir build
cd build
mkdir __arm

cmake -DCMAKE_TOOLCHAIN_FILE=../toolchain.cmake -DCMAKE_INSTALL_PREFIX=$PWD/__arm ..

make

make install
```
