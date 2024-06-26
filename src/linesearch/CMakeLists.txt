cmake_minimum_required(VERSION 3.21)
list(APPEND CMAKE_MESSAGE_CONTEXT cls)
project(linesearch VERSION 0.1.0)
set(CMAKE_C_STANDARD 11)

option(linesearch_BUILD_TESTS "Build tests for linesearch library" ON)
if (${PROJECT_IS_TOP_LEVEL} AND ${linesearch_BUILD_TESTS})
  message(STATUS "Downloading GoogleTest for testing linesearch library")
  find_package(GTest REQUIRED)
  enable_testing()
  include(GoogleTest)
  include(CTest)
endif()

add_library(linesearch_linesearch
  linesearch.cpp
  linesearch.hpp
#  linesearch.h
#  linesearch.c
  cubicspline.c
  cubicspline.h
)
target_include_directories(linesearch_linesearch
  INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/..>
)
add_library(linesearch::linesearch ALIAS linesearch_linesearch)

add_subdirectory(test)
