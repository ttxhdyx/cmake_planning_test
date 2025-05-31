cmake_minimum_required(VERSION 3.29.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
aux_source_directory(. SRC_LISTS)   #打包所有.cpp文件到SRC_LISTS
add_executable(planning_main ${SRC_LISTS}) #生成.exe文件名字为planning_main 依赖是SRC_LISTS
