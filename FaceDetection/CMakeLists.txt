cmake_minimum_required(VERSION 2.8)
project(FaceDetection CXX)
message(STATUS ${PROJECT_SOURCE_DIR}/include)
include_directories(${PROJECT_SOURCE_DIR}/include)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall -O2 -fPIC") 

file(GLOB src1_list ${PROJECT_SOURCE_DIR}/src/*.cpp)
file(GLOB src2_list ${PROJECT_SOURCE_DIR}/src/classifier/*.cpp)
file(GLOB src3_list ${PROJECT_SOURCE_DIR}/src/feat/*.cpp)
file(GLOB src4_list ${PROJECT_SOURCE_DIR}/src/io/*.cpp)
file(GLOB src5_list ${PROJECT_SOURCE_DIR}/src/util/*.cpp)
add_library(facedetection ${src1_list} ${src2_list} ${src3_list} ${src4_list} ${src5_list})

link_directories(/usr/local/lib)
add_executable(test ${PROJECT_SOURCE_DIR}/src/test/facedetection_test.cpp)
target_link_libraries(test facedetection opencv_core opencv_highgui opencv_imgproc opencv_imgcodecs)

