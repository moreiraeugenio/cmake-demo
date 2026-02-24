cmake_minimum_required(VERSION 3.28.1)

project(demo VERSION 1.0)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

include(CMakePrintHelpers)

set(SOURCE_DIR "src")
set(PARSED_SOURCE_DIR "parsed")
set(SOURCE_FILES_TARGET "${PROJECT_NAME}-source")

file(GLOB_RECURSE SOURCE_FILES "${SOURCE_DIR}/*.cpp" "${SOURCE_DIR}/*.h")
cmake_print_variables(SOURCE_FILES)
add_executable(${SOURCE_FILES_TARGET} ${SOURCE_FILES})

configure_file("${SOURCE_DIR}/${PROJECT_NAME}.h.in" "${SOURCE_DIR}/${PROJECT_NAME}.h")
target_include_directories(${SOURCE_FILES_TARGET} PUBLIC "${PROJECT_BINARY_DIR}/${SOURCE_DIR}")

# cmake_minimum_required(VERSION 3.28.1)

# project(demo VERSION 1.0)

# set(CMAKE_CXX_STANDARD 11)
# set(CMAKE_CXX_STANDARD_REQUIRED True)

# file(GLOB_RECURSE SOURCE_FILES "src/*.cpp" "src/*.h")
# set(SOURCE_FILES_TARGET ${PROJECT_NAME}-source)

# add_executable(${SOURCE_FILES_TARGET} ${SOURCE_FILES})
# configure_file("src/"${PROJECT_NAME}.h.in "src/"${PROJECT_NAME}.h)
# target_include_directories(${SOURCE_FILES_TARGET} PUBLIC ${PROJECT_BINARY_DIR})

# enable_testing()

# file(GLOB_RECURSE TEST_FILES "tests/*.cpp")
# set(TEST_FILES_TARGET ${PROJECT_NAME}-test)

# add_executable(${TEST_FILES_TARGET} ${TEST_FILES})
# target_include_directories(${TEST_FILES_TARGET} PRIVATE src)
# target_link_libraries(${TEST_FILES_TARGET} PRIVATE ${PROJECT_NAME})

# add_subdirectory(vendor/googletest)
# target_link_libraries(${TEST_FILES_TARGET} PRIVATE gtest gtest_main)

# add_test(NAME ${PROJECT_NAME}-test COMMAND ${TEST_FILES_TARGET})
