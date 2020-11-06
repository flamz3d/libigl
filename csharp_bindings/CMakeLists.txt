cmake_minimum_required(VERSION 3.1)
project(libigl_csharp_bindings)

### Conditionally compile certain modules depending on libraries found on the system
list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/../cmake)

### Compile libigl in header-only mode for Python bindings
option(LIBIGL_USE_STATIC_LIBRARY "Use LibIGL as static library" ON)

### Adding libIGL: choose the path to your local copy libIGL
if(NOT TARGET igl_common)
  include(libigl)
else()
  include(LibiglDownloadExternal)
endif()


### Output directories
if(MSVC)
  set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR})
  set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR})
else()
  set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")
endif()

add_subdirectory("iglu")