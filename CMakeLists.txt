cmake_minimum_required(VERSION 3.0)
project(Coordinate-Transform-visualization LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Eigen3 REQUIRED HINTS ${CMAKE_SOURCE_DIR}/thirdparty/Eigen3/install/share/eigen3/cmake)

if (Eigen3_FOUND)
    message(STATUS "Eigen3 Found! - ${Eigen3_DIR}")
    set(Eigen3_LIBS Eigen3::Eigen)
endif()

find_package(Pangolin REQUIRED HINTS ${CMAKE_SOURCE_DIR}/thirdparty/Pangolin/install/lib/cmake/Pangolin)

if (Pangolin_FOUND)
    message(STATUS "Pangolin Found! - ${Pangolin_DIR}")
endif()

add_executable(Coordinate-Transform-visualization 
    examples/main.cpp
)

target_include_directories(Coordinate-Transform-visualization PUBLIC
    ${Eigen3_INCLUDE_DIRS}
    ${Pangolin_INCLUDE_DIRS}
)

target_link_libraries(Coordinate-Transform-visualization PRIVATE
    ${Eigen3_LIBS}
    ${Pangolin_LIBRARIES}
)
