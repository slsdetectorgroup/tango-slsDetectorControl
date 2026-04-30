cmake_minimum_required(VERSION 3.14)
project(TangoSlsDetectorControl LANGUAGES CXX)

set(CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH};${CMAKE_CURRENT_SOURCE_DIR}/cmake")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Tango REQUIRED)
find_package(slsDetectorPackage REQUIRED)

if(slsDetectorPackage_VERSION_MAJOR LESS 8)
  message(FATAL_ERROR "slsDetectorPacakge version needs to be 8 or greater")
else()
  message(
    STATUS
      "Found slsDetectorPackage version ${slsDetectorPackage_VERSION_MAJOR}")
  add_definitions(-DSLS_MAJOR_VERSION=${slsDetectorPackage_VERSION_MAJOR})
endif()

option(SLS_DET_EMBED_RECEIVER "Embed slsReceiver in TangoDS" OFF)

if(SLS_DET_EMBED_RECEIVER)
  add_definitions(-DSLS_DET_EMBED_RECEIVER)
  find_library(
    SLS_RECEIVER_SHARED_LIB
    NAMES libSlsReceiver.so
    DOC "Path to the shared slsReceiver library")
  if(SLS_RECEIVER_SHARED_LIB)
    message(STATUS "Found slsReceiverShared: ${SLS_RECEIVER_SHARED_LIB}")
  else()
    # 1. Provide a helpful tip if it is missing
    message(
      FATAL_ERROR
        "EMBED_RECEIVER is set to ON, but the shared library 'slsReceiverShared' "
        "could not be found on your system!\n"
        "TIPP: Please ensure the slsDetectorPacakge was compiled with"
        "-DSLS_BUILD_SHARED_LIBRARIES=ON parameter and installed afterwards."
        "If it was installed in a custom directory, provide the path by passing"
        "-DCMAKE_PREFIX_PATH=/path/to/lib to CMake.\n")
  endif()
endif()
add_subdirectory(src)
