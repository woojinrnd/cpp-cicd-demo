cmake_minimum_required(VERSION 3.10)
project(CppCICD)

set(CMAKE_CXX_STANDARD 11)

add_executable(main src/main.cpp)

enable_testing()
add_executable(unit_tests tests/test_main.cpp src/main.cpp)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/release-1.12.1.zip
)
FetchContent_MakeAvailable(googletest)
target_link_libraries(unit_tests gtest_main)

include(GoogleTest)
gtest_discover_tests(unit_tests)
