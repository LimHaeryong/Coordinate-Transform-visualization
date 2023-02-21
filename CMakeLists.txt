cmake_minimum_required(VERSION 3.0)
project(Coordinate-Transform-visualization LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_subdirectory(modules)

add_executable(Coordinate-Transform-visualization 
    examples/main.cpp
)

target_link_libraries(Coordinate-Transform-visualization PRIVATE
    module1
)