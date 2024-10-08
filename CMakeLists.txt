cmake_minimum_required(VERSION 3.20)

project(Calculator)

set(CMAKE_CXX_STANDARD 20)
enable_testing()

# Set default build type if not specified
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

# Release flags (optimizations, no debug symbols)
if(CMAKE_BUILD_TYPE STREQUAL "Release")
    message("Building in Release mode with optimizations")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3 -DNDEBUG")
endif()

# Debug flags (no optimizations, debug symbols)
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    message("Building in Debug mode with debug symbols")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -O0")
endif()

# Unit test coverage flags
if(CMAKE_BUILD_TYPE STREQUAL "Coverage")
    message("Enabling coverage options")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fprofile-arcs -ftest-coverage")
    set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} --coverage")
endif()

add_subdirectory(src)
add_subdirectory(tests)
