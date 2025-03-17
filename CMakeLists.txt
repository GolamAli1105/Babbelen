cmake_minimum_required(VERSION 3.10)
project(Babbelen)

set(CMAKE_CXX_STANDARD 17)

# Set the output directory for compiled binaries
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Add source files
add_executable(Babbelen src/main.cpp)
