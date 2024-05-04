cmake_minimum_required(VERSION 3.10)
cmake_policy(SET CMP0048 NEW)
set(CMAKE_CXX_STANDARD 17)

add_library(
    sql-parser
    ""
)

target_sources(
    sql-parser
PUBLIC
    src/parser/bison_parser.cpp
    src/parser/flex_lexer.cpp
    ${CMAKE_CURRENT_LIST_DIR}/src/parser/flex_lexer.h
    ${CMAKE_CURRENT_LIST_DIR}/src/parser/bison_parser.h
)

target_include_directories(
    sql-parser
    PUBLIC ${CMAKE_CURRENT_LIST_DIR}/src
)
