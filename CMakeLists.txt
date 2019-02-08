cmake_minimum_required(VERSION 3.2)

include(cmake/HunterGate.cmake)

HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.23.98.tar.gz"
    SHA1 "bf539cb70375ac319e386ae2ec5b5a0c4923480a"
)

project(block-planner)

add_executable(
    "${PROJECT_NAME}"
    main.cc
)
