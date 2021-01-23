cmake_minimum_required(VERSION 3.16.3)

project(CMAKE_LESSONS)

add_executable(${PROJECT_NAME} main.c )

set(list_subdirs "")

function(smtg_add_subdirectories)
    message("")
    message("Adding the subdirectories...")
    file(GLOB subDirectories RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *)
    foreach(dir ${subDirectories})
        if(IS_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/${dir}")
            if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/${dir}/CMakeLists.txt")
                message("Adding ${dir} as a subdirectory!")
                add_subdirectory(${dir})
                list(APPEND list_subdirs "${dir}")
                set(list_subdirs ${list_subdirs} PARENT_SCOPE)
            endif()
        endif()
    endforeach()
    message("")
endfunction()

smtg_add_subdirectories()

target_include_directories(${PROJECT_NAME} PRIVATE ${list_subdirs})

target_link_directories(${PROJECT_NAME} PRIVATE ${list_subdirs})

target_link_libraries(${PROJECT_NAME} adderL suberL)
