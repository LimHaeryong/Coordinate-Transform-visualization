cmake_minimum_required(VERSION 3.0)
project(module1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(MODULE1_SOURCE_FILES
    src/PlotTrajectory.cpp
)

add_library(module1 
    ${MODULE1_SOURCE_FILES}
)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_MODULE_PATH})
find_package(Eigen3 REQUIRED HINTS ${CMAKE_SOURCE_DIR}/thirdparty/Eigen3/install/share/eigen3/cmake)
find_package(Pangolin REQUIRED HINTS ${CMAKE_SOURCE_DIR}/thirdparty/Pangolin/install/lib/cmake/Pangolin)

if (Eigen3_FOUND)
    message(STATUS "Eigen3 Found! - ${Eigen3_DIR}")
    set(Eigen3_LIBS Eigen3::Eigen)
endif()

if (Pangolin_FOUND)
    message(STATUS "Pangolin Found! - ${Pangolin_DIR}")
endif()

target_include_directories(module1 PUBLIC
    include
    ${Eigen3_INCLUDE_DIRS}
    ${Pangolin_INCLUDE_DIRS}
)

target_link_libraries(module1 PUBLIC
    ${Eigen3_LIBS}
    ${Pangolin_LIBRARIES}
)