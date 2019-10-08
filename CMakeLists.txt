cmake_minimum_required(VERSION 3.12)
project(mtlpp_lib_project)

set(CMAKE_CXX_STANDARD 17)

add_library(mtlpp_lib
        mtlpp.mm
        )

target_link_libraries(mtlpp_lib
        )

target_include_directories(mtlpp_lib
        PRIVATE

        PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}
        )
