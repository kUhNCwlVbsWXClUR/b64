
cmake_minimum_required(VERSION 3.0)

project(cJSON)


#cJSON
set(BASE64_LIB b64)

file(GLOB HEADERS ${PROJECT_SOURCE_DIR}/include/b64/*.h)
#set(SOURCES src/*.c)
file(GLOB SOURCES src/*.c)

include_directories(${PROJECT_SOURCE_DIR}/include/)


# See https://cmake.org/Wiki/CMake_FAQ#How_do_I_make_my_shared_and_static_libraries_have_the_same_root_name.2C_but_different_suffixes.3F
add_library("${BASE64_LIB}" SHARED "${HEADERS}" "${SOURCES}")
add_library("${BASE64_LIB}-static" STATIC "${HEADERS}" "${SOURCES}")
set_target_properties("${BASE64_LIB}-static" PROPERTIES OUTPUT_NAME "${BASE64_LIB}")
set_target_properties("${BASE64_LIB}-static" PROPERTIES PREFIX "lib")


add_subdirectory(tests)
