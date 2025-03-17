cmake_minimum_required(VERSION 3.10)
project(Babbelen)

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_PREFIX_PATH "C:/vcpkg/installed/x64-windows")
set(CMAKE_TOOLCHAIN_FILE "C:/vcpkg/scripts/buildsystems/vcpkg.cmake" CACHE STRING "Vcpkg toolchain file")

set(Boost_INCLUDE_DIR "C:/vcpkg/installed/x64-windows/include")
set(Boost_LIBRARY_DIR "C:/vcpkg/installed/x64-windows/lib")

# Set the output directory for compiled binaries
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/bin)

include_directories("C:/vcpkg/installed/x64-windows/include")

include_directories(${Boost_INCLUDE_DIR})
link_directories(${Boost_LIBRARY_DIR})

# Add source files
add_executable(Babbelen src/main.cpp src/server.cpp)

if(POLICY CMP0167)
  cmake_policy(SET CMP0167 NEW)
endif()

find_package(Boost REQUIRED COMPONENTS system filesystem)
find_package(OpenSSL REQUIRED)

include_directories(${Boost_INCLUDE_DIRS})
# Link Boost and OpenSSL to your executable
target_link_libraries(Babbelen PRIVATE Boost::system Boost::filesystem OpenSSL::SSL OpenSSL::Crypto)