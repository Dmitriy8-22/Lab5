cmake_minimum_required(VERSION 3.14)

project(banking_tests)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Автоматически скачиваем Google Test и Google Mock
include(FetchContent)

FetchContent_Declare(
    googletest
    GIT_REPOSITORY https://github.com/google/googletest.git
    GIT_TAG release-1.11.0
)

FetchContent_MakeAvailable(googletest)

# Создаем тестовый исполняемый файл
add_executable(run_tests
    main.cpp
    test_account.cpp
    test_transaction.cpp
    ../Account.cpp
    ../Transaction.cpp
)

# Линкуем с Google Test и Google Mock
target_link_libraries(run_tests
    gtest_main
    gmock
)

# Добавляем директорию с заголовочными файлами
target_include_directories(run_tests PRIVATE ..)

# Включаем тесты
include(GoogleTest)
gtest_discover_tests(run_tests)

