cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(Sample)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/Modules/")
find_package(Leap REQUIRED)

include_directories(${LEAP_INCLUDE_DIRS})
include_directories(${CMAKE_SOURCE_DIR}/include)

add_executable (Sample
	src/Sample.cpp
)

target_link_libraries (Sample ${LEAP_LIBRARIES} -lz)

#find_package(OpenCV 2.4.10 REQUIRED)
#include_directories(${OpenCV_INCLUDE_DIRS})
#add_subdirectory(${CMAKE_SOURCE_DIR}/src/LeapVisualizerOpenCV)

add_subdirectory(src)
