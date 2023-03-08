cmake_minimum_required(VERSION 3.20)
project(Anemone)

# Anemone最终编译成so动态库 设置动态库的路径 放置项目根目录的lib文件夹下面
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

# 设置调试信息  以及启动C++11语言标准
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -std=c++11")

# 定义参与编译的源代码文件
aux_source_directory(. SRC_LIST)

include_directories(${PROJECT_SOURCE_DIR})

# 编译动态库
add_library(Anemone SHARED ${SRC_LIST})

add_executable(test example/testserver.cc)

target_link_libraries(test Anemone)
