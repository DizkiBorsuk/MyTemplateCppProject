cmake_minimum_required(VERSION 3.20)
project(template_project VERSION 0.1.0 LANGUAGES CXX)

set(CMAKE_BUILD_TYPE Release)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_FLAGS "-std=c++20 -Wall")
set(CMAKE_CXX_FLAGS_RELEASE  "-std=c++20 -O3 -fopenmp -pthread")

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR})
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

############### dependencies ######################
find_package(Eigen3  REQUIRED NO_MODULE)
find_package(OpenCV  REQUIRED)
find_package(Matplot++ REQUIRED)

include_directories(${OpenCV_INCLUDE_DIRS})

set(THIRD_PARTY_LIBS
        ${OpenCV_LIBS}
        pthread
        Eigen3::Eigen 
        Matplot++::matplot
        )

include_directories(${PROJECT_SOURCE_DIR}/include)
add_subdirectory(src)

add_executable(run_project main.cpp)
target_link_libraries(run_project template_lib)