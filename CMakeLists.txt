cmake_minimum_required (VERSION 2.8)
project(velo)

set(CMAKE_MODULE_PATH ".")
find_package(PCL 1.8 REQUIRED)
find_package(OpenCV 3.0 REQUIRED)
find_package(Ceres REQUIRED)
find_package(Glog REQUIRED)
include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})
include_directories(${OpenCV_INCLUDE_DIRS})
link_directories(${OpenCV_LIBRARY_DIRS})
add_definitions(${OpenCV_DEFINITIONS})
link_directories(${Ceres_LIBRARY_DIRS})
add_definitions(${Ceres_DEFINITIONS})
include_directories(${Glog_INCLUDE_DIRS})
link_directories(${Glog_LIBRARY_DIRS})
add_definitions(${Glog_DEFINITIONS})
include_directories(${CHOLMOD_INCLUDE_DIR})
link_libraries(${CHOLMOD_LIBRARY_DIR})

set(CMAKE_MODULE_PATH "/home/dllu/sync/proj/isam/isam/cmake")
include_directories("/usr/local/include/ceres")
include_directories("/usr/local/include/isam/")
include_directories("/usr/local/include/")

add_executable(main main.cpp)
target_link_libraries(main isam cholmod ${CERES_LIBRARIES} ${Glog_LIBRARIES} ${PCL_LIBRARIES} ${OpenCV_LIBRARIES})
set_target_properties(main PROPERTIES COMPILE_FLAGS "-DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_FLAGS=-O3")
#set_target_properties(main PROPERTIES COMPILE_FLAGS "-DCMAKE_BUILD_TYPE=Debug -DCMAKE_CXX_FLAGS=-g -O0")
