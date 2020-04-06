## GENERAL PROJECT SETTINGS
cmake_minimum_required(VERSION 3.14)

project("gfak"
        VERSION 0.1
        LANGUAGES C CXX)

## PROJECT OPTIONS

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Debug" CACHE STRING "Choose the type of build, options are: Debug Release" FORCE)
    message(STATUS "Defaulting build type set to 'Debug'")
endif()
message(STATUS "Build type: ${Green}${CMAKE_BUILD_TYPE}${ColorReset}")

# If the user does not specify PREFIX, we default to ${CMAKE_BINARY_DIR} instead of system directory /usr
if (CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    set(CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}/install" CACHE PATH "Default install path (prefix)" FORCE)
endif()

## COMPILERS

set(CMAKE_CXX_STANDARD 11)

set(FLAGS_WARN "-Wall -Wextra -Wno-unused-parameter -Wno-unused-variable")
set(CMAKE_C_FLAGS "${FLAGS_WARN}")
set(CMAKE_CXX_FLAGS "${FLAGS_WARN} -O3 -pipe -fPIC -march=native -mtune=native")

## DEPENDENCIES

## Global include directories
include_directories(${PROJECT_SOURCE_DIR}/src/tinyFA ${PROJECT_SOURCE_DIR}/src/tinyFA/pliib ${PROJECT_SOURCE_DIR}/src)

## TARGETS
add_executable(gfak ${PROJECT_SOURCE_DIR}/src/main.cpp)
