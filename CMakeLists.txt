cmake_minimum_required(VERSION 2.8.11)

set(PROJECT "testLink")
project(${PROJECT})

# lib
file(GLOB hdrs "${CMAKE_SOURCE_DIR}/include/*.h")
file(GLOB srcs "${CMAKE_SOURCE_DIR}/src/*.cpp")
add_library(myLib ${srcs} ${hdrs})
target_include_directories(myLib PUBLIC "${CMAKE_SOURCE_DIR}/include")

# main
file(GLOB srcs "${CMAKE_SOURCE_DIR}/application/*.cpp")
add_executable(main ${srcs})
target_include_directories(main PUBLIC "${CMAKE_SOURCE_DIR}/include")
target_link_libraries(main myLib)