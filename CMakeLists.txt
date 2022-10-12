cmake_minimum_required(VERSION 3.23)
project(ICP)

set(CMAKE_CXX_STANDARD 17)

if(NOT TARGET kdtree)
    add_subdirectory(external/KDTree)
endif()

find_package(Eigen3 REQUIRED)

add_library(${PROJECT_NAME} src/ICP.cpp)

target_include_directories(${PROJECT_NAME} PUBLIC include)

target_link_libraries(${PROJECT_NAME} PRIVATE Eigen3::Eigen PRIVATE kdtree)

install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION lib)
