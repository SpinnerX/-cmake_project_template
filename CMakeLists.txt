cmake_minimum_required(VERSION 3.15)
set(PROJECT_NAME Example_Project_Template)
project(${PROJECT_NAME} VERSION 0.1.0 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_FLAGS "-Wno-dev")
set(CMAKE_CXX_FLAGS "-fno-exceptions" "-fsanitize=address" "-Wall" "-Wextra")
set(CMAKE_CXX_FLAGS "-std=c++20")
set(PROJECT_INCLUDE_DIR TemplateProject)

add_compile_options(-fsanitize=address)
add_link_options(-fsanitize=address)

# CMake that handles precompiled headers
include(cmake/precompiled_headers.cmake)

# Setting include directories and where to find the header files
include_directories(
    ${PROJECT_SOURCE_DIR}/TemplateProject/include
)

set(
    all_src
    ${PROJECT_SOURCE_DIR}/${PROJECT_INCLUDE_DIR}/src/${PROJECT_INCLUDE_DIR}/Core.cpp
)

add_subdirectory(Sandbox)

add_precompiled_header(${PROJECT_NAME} include/PrecompiledHeader.h FORCEINCLUDE SOURCE_CXX src/PrecompiledHeader.cpp)

add_library(${PROJECT_NAME} SHARED ${all_src})
add_library(Engine::Engine ALIAS ${PROJECT_NAME}) # Allows to alias the library

set_property(TARGET ${PROJECT_NAME} PROPERTY INTERPROCEDURAL_OPTIMIZATION True)

# Linking the included directories
target_include_directories(
  ${PROJECT_NAME}
  PUBLIC
  ${PROJECT_SOURCE_DIR}/GameEngine/include
  ${PROJECT_SOURCE_DIR}/GameEngine/include/GameEngine
)

# This is how you can have precompiled headers
# This allows for faster compile time
target_precompile_headers(${PROJECT_NAME} PRIVATE
  "$<$<COMPILE_LANGUAGE:CXX>:${CMAKE_CURRENT_SOURCE_DIR}/TemplateProject/include/PrecompiledHeaders.h>"
)