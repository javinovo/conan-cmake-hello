cmake_minimum_required(VERSION 3.10)

project(hello-consumer CXX)

# Setup Conan packages ('conan install' must be run first)
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_executable(main main.cpp)
target_link_libraries(main ${CONAN_LIBS})
