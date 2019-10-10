cmake_minimum_required(VERSION 3.12)
project(mtlpp_lib_project)

set(CMAKE_CXX_STANDARD 17)

add_library(mtlpp_lib
        mtlpp.mm
        )

#set_target_properties(mtlpp_lib PROPERTIES PUBLIC_HEADER mtlpp.hpp)

target_link_libraries(mtlpp_lib
        "-framework Metal"
        "-framework MetalKit"
        "-framework Cocoa"
        "-framework CoreFoundation"
        )

target_include_directories(mtlpp_lib
        PRIVATE

        PUBLIC
                $<INSTALL_INTERFACE:include>
                $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}>
        )

if (FALSE) # only required when installing the lib
  add_executable(00_init
          examples/00_init.cpp)

  target_link_libraries(00_init
          mtlpp_lib)

  install(TARGETS mtlpp_lib EXPORT mtlpp_lib DESTINATION lib)
  install(EXPORT mtlpp_lib DESTINATION lib)
  install(FILES mtlpp.hpp
          DESTINATION include)
endif()
