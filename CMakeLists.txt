PROJECT(sqlite3)
cmake_minimum_required(VERSION 3.24)

set(SQLITE3_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/src/sqlite3.c
					${CMAKE_CURRENT_SOURCE_DIR}/src/sqlite3.h
					${CMAKE_CURRENT_SOURCE_DIR}/src/sqlite3ext.h)
add_library(sqlite3 STATIC ${SQLITE3_SOURCES})
add_library(sqlite3::sqlite3 ALIAS sqlite3)
target_include_directories(sqlite3 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
target_compile_definitions(sqlite3 PRIVATE SQLITE_ENABLE_RTREE
        SQLITE_ENABLE_FTS4
        SQLITE_ENABLE_FTS5
        SQLITE_ENABLE_JSON1
        SQLITE_ENABLE_RBU
        SQLITE_ENABLE_STAT4
)

install(FILES src/sqlite3.h src/sqlite3ext.h DESTINATION include)
