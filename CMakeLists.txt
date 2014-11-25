cmake_minimum_required(VERSION 2.6)
set(PROJECT_NAME c_project_template)
set(PROJ_VERSION 0.0.1)
project(${PROJECT_NAME})
enable_testing()
set(CMAKE_VERBOSE_MAKEFILE 0)

# Enabke debug mode if not release is comming
if (NOT CMAKE_BUILD_TYPE MATCHES release)
    set(CMAKE_BUILD_TYPE debug)
endif()
message("CMAKE_BUILD_TYPE = ${CMAKE_BUILD_TYPE}")

# Make compaining compiler if gcc
if(CMAKE_COMPILER_IS_GNUCC)
    add_definitions(-Wall -Werror -ansi -pedantic -std=c99)
endif(CMAKE_COMPILER_IS_GNUCC)

FIND_PACKAGE(Threads)

# Add Include directories
include_directories(src/include)

# Libraries being used
find_package(PkgConfig REQUIRED)
pkg_check_modules(THIRDPARTY REQUIRED glib-2.0)
include_directories(${THIRDPARTY_INCLUDE_DIRS})
link_directories(${THIRDPARTY_LIBRARY_DIRS})
add_definitions(${THIRDPARTY_OTHERS})

# Copy (or set path for data)

# Source code dirs
add_subdirectory(src)

