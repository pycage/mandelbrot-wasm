cmake_minimum_required(VERSION 3.0)
project(mandelbrot-wasm)

# check, if we're in an Emscripten environment
if("$ENV{EMSDK}" STREQUAL "")
  message(FATAL_ERROR "Please install and initialize the Emscripten SDK -- https://emscripten.org")
else()
  message(STATUS "Found Emscripten SDK in $ENV{EMSDK}")
endif()

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_subdirectory(src)
add_subdirectory(www)
