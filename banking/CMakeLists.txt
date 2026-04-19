cmake_minimum_required(VERSION 3.14)

project(banking)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(banking STATIC
    Account.cpp
    Transaction.cpp
)

target_include_directories(banking PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

if(ENABLE_COVERAGE)
    target_compile_options(banking PRIVATE --coverage -g -O0)
    target_link_options(banking PRIVATE --coverage)
endif()
