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

set(SQL_PARSER_CMAKE_DIR ${CMAKE_INSTALL_LIBDIR}/cmake/quill CACHE STRING
       "Installation directory for cmake files, relative to ${CMAKE_INSTALL_PREFIX}.")
set(SQL_PARSER_LIB_DIR ${CMAKE_INSTALL_LIBDIR} CACHE STRING
       "Installation directory for libraries, relative to ${CMAKE_INSTALL_PREFIX}.")
set(SQL_PARSER_INC_DIR ${CMAKE_INSTALL_INCLUDEDIR} CACHE STRING
       "Installation directory for include files, relative to ${CMAKE_INSTALL_PREFIX}.")

install(TARGETS sql-parser EXPORT sql-parser
            LIBRARY DESTINATION ${SQL_PARSER_LIB_DIR}
            ARCHIVE DESTINATION ${SQL_PARSER_LIB_DIR}
            RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR})
