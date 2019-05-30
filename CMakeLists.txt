cmake_minimum_required(VERSION 3.14 FATAL_ERROR)
project(chippy VERSION 0.1 LANGUAGES CXX)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(GNUInstallDirs)

enable_testing()
add_subdirectory(src)
add_subdirectory(test)