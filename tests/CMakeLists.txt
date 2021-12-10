
set(TEST_NAME test_base64)

add_executable(${TEST_NAME} base64.cc)

target_link_libraries(${TEST_NAME} ${BASE64_LIB})
