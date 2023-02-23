cmake_minimum_required(VERSION 3.25)

set(CMAKE_CXX_STANDARD 20)

# Code to enable CMake C++ Modules.
# All of this modules-related code is gathered from https://www.kitware.com/import-cmake-c20-modules/.

## Turn on the dynamic depends for ninja.
set(CMAKE_EXPERIMENTAL_CXX_MODULE_DYNDEP 1)

## Turn on the experimental API.
set(CMAKE_EXPERIMENTAL_CXX_MODULE_CMAKE_API  "2182bf5c-ef0d-489a-91da-49dbc3090d2a")

## C++ Modules CMake tests.
set(CMake_TEST_CXXModules_UUID "a246741c-d067-4019-a8fb-3d16b0c9d1d3")

## C++ Modules configuration code.
set(CMAKE_EXPERIMENTAL_CXX_MODULE_DYNDEP 1)
string(CONCAT CMAKE_EXPERIMENTAL_CXX_SCANDEP_SOURCE
  "<CMAKE_CXX_COMPILER> <DEFINES> <INCLUDES> <FLAGS> -E -x c++ <SOURCE>"
  " -MT <DYNDEP_FILE> -MD -MF <DEP_FILE>"
  " -fmodules-ts -fdep-file=<DYNDEP_FILE> -fdep-output=<OBJECT> -fdep-format=trtbd"
  " -o <PREPROCESSED_SOURCE>")
set(CMAKE_EXPERIMENTAL_CXX_MODULE_MAP_FORMAT "gcc")
set(CMAKE_EXPERIMENTAL_CXX_MODULE_MAP_FLAG "-fmodules-ts -fmodule-mapper=<MODULE_MAP_FILE> -fdep-format=trtbd -x c++")

set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

project(Test
  VERSION 1.0
  DESCRIPTION "Test CMake build."
  LANGUAGES CXX)

add_executable(Test source/Main.cpp)