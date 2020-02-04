cmake_minimum_required(VERSION 3.10)
project(RxCppAsioReproduction)

set(CMAKE_CXX_STANDARD 14)

find_package(Threads)

if(EXISTS /opt/boost_1_71_0)
    set(BOOST_ROOT /opt/boost_1_71_0)
endif()
find_package(Boost 1.71 REQUIRED COMPONENTS system thread)
include_directories(${Boost_INCLUDE_DIRS})

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake-extras/")

find_package(rxcpp CONFIG)

set(COMMON_LIBRARIES
        ${Boost_LIBRARIES}
        ${CMAKE_THREAD_LIBS_INIT})

add_executable(RxCppAsioTimeout
        main_rxcpp_asio_timeout.cpp
        rx-asio.h)
target_compile_definitions(RxCppAsioTimeout PRIVATE _GNU_SOURCE)
# note cudaWrapper is comming from add_subdirectory("CudaPictureFilter")
target_link_libraries(RxCppAsioTimeout ${COMMON_LIBRARIES})
