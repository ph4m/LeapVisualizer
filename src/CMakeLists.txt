cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(LeapVisualizer)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")


set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/Modules/")
find_package(Leap REQUIRED)

include_directories(${LEAP_INCLUDE_DIRS})
include_directories(${CMAKE_SOURCE_DIR}/include)

#add_library (DepthSenseGrabberCore SHARED
add_library (LeapVisualizerCore SHARED
	LeapVisualizerCore.cpp
    LeapVisualizerCore.h
)

#GENERATE_EXPORT_HEADER( DepthSenseGrabberCore
#             BASE_NAME DepthSenseGrabberCore
#             EXPORT_MACRO_NAME DepthSenseGrabberCore_EXPORT
#             EXPORT_FILE_NAME DepthSenseGrabberCore_Export.h
#             STATIC_DEFINE DepthSenseGrabberCore_BUILT_AS_STATIC
#)

target_link_libraries (LeapVisualizerCore ${LEAP_LIBRARIES})# -lz ${Boost_LIBRARIES})

add_executable (LeapVisualizerPrint
    LeapVisualizerPrint.cpp
    LeapVisualizerCore.h
)
target_link_libraries (LeapVisualizerPrint LeapVisualizerCore)



find_package(OpenCV 2.4.10 REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})
add_executable (LeapVisualizerOpenCV
	LeapVisualizerOpenCV.cpp
)
target_link_libraries (LeapVisualizerOpenCV ${LEAP_LIBRARIES} -lz ${OpenCV_LIBS})
