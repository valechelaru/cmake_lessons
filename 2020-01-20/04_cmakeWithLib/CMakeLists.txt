cmake_minimum_required(VERSION 3.16.3)

project(CMAKE_LESSONS)

add_executable(${PROJECT_NAME} main.c )

add_subdirectory(AdderLib)

target_include_directories(${PROJECT_NAME} PUBLIC AdderLib)

target_link_directories(${PROJECT_NAME} PRIVATE AdderLib)

target_link_libraries(${PROJECT_NAME} adderL)
