add_definitions(-DMONGOCXX_TESTING)

set(mongocxx_test_srcs
    bulk_write.cpp
    client.cpp
    CMakeLists.txt
    collection.cpp
    database.cpp
    model/update_many.cpp
    options/aggregate.cpp
    private/write_concern.cpp
    result/delete.cpp
    result/insert_one.cpp
    result/replace_one.cpp
    result/update.cpp
    write_concern.cpp
)

include_directories(
    ${CMAKE_SOURCE_DIR}/src/third_party/catch/include
)

link_directories(${LIBMONGOC_LIBRARY_DIRS} ${LIBBSON_LIBRARY_DIRS})

add_executable(test_driver
    ${CMAKE_SOURCE_DIR}/src/third_party/catch/main.cpp
    ${test_driver_sources}
)

target_link_libraries(test_driver mongocxx_mocked)
add_test(driver test_driver)