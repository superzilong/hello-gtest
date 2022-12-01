cmake_minimum_required(VERSION 3.0.0)
project(hello_gtest VERSION 0.1.0)

# GoogleTest requires at least C++14
set(CMAKE_CXX_STANDARD 14)

include(FetchContent)
FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG release-1.12.1
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)


# include(CTest)
enable_testing()

add_executable(hello_gtest main.cpp)

target_link_libraries(
  hello_gtest
  GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(hello_gtest)

