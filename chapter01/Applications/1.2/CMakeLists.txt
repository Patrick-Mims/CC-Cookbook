cmake_minimum_required(VERSION 3.22)

project(main VERSION 1.0)

option(USE_MYMATH "Use tutorial provided math implementation" ON)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/inc)

#configure_file("${PROJECT_SOURCE_DIR}/src/config.h.in" "${PROJECT_BINARY_DIR}/config.h")
include_directories("${PROJECT_BINARY_DIR}")

add_subdirectory(impl)

file(GLOB SOURCES "src/main.cc")

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED NO)
set(CMAKE_BUILD_TYPE debug)
set(CMAKE_CXX_EXTENSIONS NO)

#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++20")

add_executable(${PROJECT_NAME} ${SOURCES})

target_link_libraries(main PUBLIC impl)

target_include_directories(main PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}/impl")
