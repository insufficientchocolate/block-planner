cmake_minimum_required(VERSION 3.2)

include(cmake/HunterGate.cmake)

HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.23.98.tar.gz"
    SHA1 "bf539cb70375ac319e386ae2ec5b5a0c4923480a"
)

project(block-planner)

hunter_add_package(Qt)

find_package(Qt5Core CONFIG REQUIRED)
find_package(Qt5Widgets CONFIG REQUIRED)
find_package(Qt5PrintSupport CONFIG REQUIRED)

add_executable(
    "${PROJECT_NAME}"
    main.cc
)

target_link_libraries("${PROJECT_NAME}" Qt5::Core Qt5::Widgets Qt5::PrintSupport)

if(APPLE)
    find_library(SECURITY_FRAMEWORK Security)
    if(NOT SECURITY_FRAMEWORK)
        message(FATAL_ERROR "unable to find security framework")
    endif()
    target_link_libraries("${PROJECT_NAME}" "${SECURITY_FRAMEWORK}")
endif()
