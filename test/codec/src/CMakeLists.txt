set(TEST_NAME codec)

add_executable(tester_${TEST_NAME} tester_${TEST_NAME}.cpp tester_bitserializer.cpp)

set_target_properties(tester_${TEST_NAME} PROPERTIES FOLDER test/ddl)  
set_target_properties(tester_${TEST_NAME}  PROPERTIES TIMEOUT 300)

target_link_libraries(tester_${TEST_NAME} PRIVATE
    ddl
    a_util_result
    GTest::Main
    $<$<PLATFORM_ID:Linux>:Threads::Threads>
)
add_test(tester_${TEST_NAME} tester_${TEST_NAME})

set(TEST_NAME mediacoder_regression)
add_executable(tester_${TEST_NAME} tester_${TEST_NAME}.cpp)
add_test(NAME tester_${TEST_NAME} 
         COMMAND tester_${TEST_NAME}
         WORKING_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/../"
         )

set_target_properties(tester_${TEST_NAME} PROPERTIES FOLDER test/ddl)  
set_target_properties(tester_${TEST_NAME}  PROPERTIES TIMEOUT 300)

target_link_libraries(tester_${TEST_NAME} PRIVATE
    ddl_test_compat
    ddl
    a_util_result
    GTest::Main
    $<$<PLATFORM_ID:Linux>:Threads::Threads>
)
