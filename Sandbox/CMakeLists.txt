cmake_minimum_required(VERSION 3.15)
set(PROJECT_NAME Sandbox)
project(${PROJECT_NAME} VERSION 0.1.0 LANGUAGES C CXX)


set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_FLAGS "-Wno-dev")
set(CMAKE_CXX_FLAGS "-fno-exceptions" "-fsanitize=address" "-Wall" "-Wextra")
set(CMAKE_CXX_FLAGS "-std=c++20")

add_compile_options(-fsanitize=address)
add_link_options(-fsanitize=address)

add_executable(${PROJECT_NAME} main.cpp)

set_property(TARGET ${PROJECT_NAME} PROPERTY INTERPROCEDURAL_OPTIMIZATION True)