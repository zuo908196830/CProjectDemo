cmake_minimum_required(VERSION 3.16)

project(demo C)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)

add_library(test_fun
    src/test_fun/t_add.c
)

target_include_directories(test_fun PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

add_library(mh
    src/mh/mh_add.c
)

target_include_directories(mh PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_link_libraries(mh
    test_fun
)

add_executable(demo
    src/main.c
)

target_link_libraries(demo
    mh
)