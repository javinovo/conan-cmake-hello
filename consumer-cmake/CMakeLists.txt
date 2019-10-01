cmake_minimum_required(VERSION 3.10)

project(hello-consumer-cmake CXX)

# Download automatically, you can also just copy the conan.cmake file
if(NOT EXISTS "${CMAKE_BINARY_DIR}/conan.cmake")
   message(STATUS "Downloading conan.cmake from https://github.com/conan-io/cmake-conan")
   file(DOWNLOAD "https://raw.githubusercontent.com/conan-io/cmake-conan/master/conan.cmake"
                  "${CMAKE_BINARY_DIR}/conan.cmake")
endif()
include(${CMAKE_BINARY_DIR}/conan.cmake)

# Install packages
conan_cmake_run(REQUIRES Hello/0.1@demo/testing
                BASIC_SETUP)

add_executable(main example.cpp)
target_link_libraries(main ${CONAN_LIBS})
