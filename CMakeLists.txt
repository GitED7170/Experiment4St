#CMake 4.x 起不再兼容 <3.5；googletest 自身也要求 3.5，故此处取 3.5
cmake_minimum_required(VERSION 3.5)

#设置 C/C++ 编译器为课程统一工具链 MinGW-w64 8.1.0
#必须在 PROJECT() 之前设置，避免 PATH 中其它 g++（如 MSYS2 的 15.2.0）被抢先选用
#对应 PDF 第 7.2 节 “在 CMakeLists.txt 里添加这样一行来设置编译器”
set(CMAKE_C_COMPILER   "D:/Turing machine/Documents/mingw64/bin/gcc.exe")
set(CMAKE_CXX_COMPILER "D:/Turing machine/Documents/mingw64/bin/g++.exe")

PROJECT("Experiment4St")

SET(CMAKE_CXX_STANDARD 17)
SET(CMAKE_CXX_FLAGS "-Wno-deprecated-declarations -Wall -Werror -Wnon-virtual-dtor -Woverloaded-virtual")

#可执行文件输出目录
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#构建的库的输出目录
SET(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin) 

#构建test 目标
ENABLE_TESTING()
#向当前项目添加一个子目录，并且使得 CMake 在构建过程中进入该子目录继续处理其中的 CMakeLists.txt 文件。
#这个命令通常用于管理项目中的多个模块或子项目。
ADD_SUBDIRECTORY(src)
ADD_SUBDIRECTORY(tests)
