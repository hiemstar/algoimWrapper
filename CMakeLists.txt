cmake_minimum_required(VERSION 3.15)

project(algoimWrapper)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} --std=c++17 -W -Wall -O3 -DNDEBUG")
SET(JlCxx_DIR "/home/rene/cpp-projects/libcxxwrap-julia-build")

SET(Julia_EXECUTABLE "/opt/julia-1.8.5/bin/julia")

find_package(JlCxx REQUIRED)
find_package(BLAS REQUIRED)
# find_package(LAPACK REQUIRED)

# find_package(BLAS REQUIRED)
# find_package(BLAS REQUIRED)


add_subdirectory(ext)

include_directories(${CMAKE_SOURCE_DIR})

add_library(algoimwrapper SHARED src/algoimwrapper.cpp)

target_link_libraries(algoimwrapper JlCxx::cxxwrap_julia BLAS::BLAS)

install(TARGETS
  algoimwrapper
LIBRARY DESTINATION lib
ARCHIVE DESTINATION lib
RUNTIME DESTINATION lib)