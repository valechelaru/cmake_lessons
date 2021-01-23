cmake_minimum_required(VERSION 3.16.3)

project(CMAKE_LESSONS)

# set(CMAKE_CURRENT_BINARY_DIR ${CMAKE_CURRENT_SOURCE_DIR}/build)

add_executable(${PROJECT_NAME} main.c )

add_subdirectory(AdderLib)

add_subdirectory(SubLib)

message(${CMAKE_CURRENT_BINARY_DIR})

target_include_directories(${PROJECT_NAME} PRIVATE AdderLib SubLib)

target_link_directories(${PROJECT_NAME} PRIVATE AdderLib SubLib)

target_link_libraries(${PROJECT_NAME} adderL suberL)
