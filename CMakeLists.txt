cmake_minimum_required(VERSION 3.1)

project(algoimWrapper)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} --std=c++17 -W -Wall -O3 -DNDEBUG")

find_package(JlCxx REQUIRED)
find_package(BLAS REQUIRED)

include_directories(${CMAKE_SOURCE_DIR})

add_library(algoimwrapper SHARED src/algoimwrapper.cpp)

target_link_libraries(algoimwrapper JlCxx::cxxwrap_julia openblas)

install(TARGETS
  algoimwrapper
LIBRARY DESTINATION lib
ARCHIVE DESTINATION lib
RUNTIME DESTINATION lib)