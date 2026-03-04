cmake_minimum_required(VERSION 3.14)
project(TangoSlsDetectorControl LANGUAGES CXX)

set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH};${CMAKE_CURRENT_SOURCE_DIR}/cmake")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Tango REQUIRED)
find_package(slsDetectorPackage REQUIRED)

if (slsDetectorPackage_VERSION_MAJOR LESS 8)
        message(FATAL_ERROR "slsDetectorPacakge version needs to be 8 or greater")
else()
    message(STATUS "Found slsDetectorPackage version ${slsDetectorPackage_VERSION_MAJOR}")
    add_definitions(-DSLS_MAJOR_VERSION=${slsDetectorPackage_VERSION_MAJOR})
endif()

add_subdirectory(src)
