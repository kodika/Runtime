cmake_minimum_required(VERSION 3.16)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules)

project(Runtime
  LANGUAGES C Swift)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_Swift_MODULE_DIRECTORY ${CMAKE_BINARY_DIR}/swift)

include(SwiftSupport)

option(BUILD_SHARED_LIBS "build shared libraries" ON)

find_package(dispatch CONFIG REQUIRED)
find_package(Foundation CONFIG REQUIRED)

add_subdirectory(Sources)

export(EXPORT Runtime
  FILE RuntimeConfig.cmake)
  
export(EXPORT CRuntime
    FILE CRuntimeConfig.cmake)