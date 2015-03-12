cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(LeapVisualizerOpenCV)

add_executable (LeapVisualizerOpenCV
	LeapVisualizerOpenCV.cpp
)

target_link_libraries (LeapVisualizerOpenCV ${LEAP_LIBRARIES} -lz ${OpenCV_LIBS})
