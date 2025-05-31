cmake_minimum_required(VERSION 3.29.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)

# 变量和目录设置
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin) # 把动态库和exe文件都指定到bin文件夹下
#CMAKE_LIBRARY_OUTPUT_DIRECTORY Linux下用这个
#CMAKE_ARCHIVE_OUTPUT_DIRECTORY 只把静态库的目录指出来

# 动态库
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS) 
add_library(
    common
    SHARED
    ${SRC_LISTS}
)
target_include_directories(
    common
    PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

# 可执行文件
add_executable(planning_main planning_main.cpp) #生成.exe文件名字为planning_main 依赖是SRC_LISTS

target_include_directories(
    planning_main
    PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)
target_link_libraries(
    planning_main
    PUBLIC
    common
)
