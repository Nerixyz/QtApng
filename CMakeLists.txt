cmake_minimum_required(VERSION 3.20)
cmake_policy(SET CMP0077 NEW)

project(
  QtApng
  VERSION 0.1.0
  LANGUAGES CXX)

option(APNG_TESTS "Enable tests" OFF)
option(APNG_EXAMPLES "Enable examples" OFF)
option(APNG_QT6 "Build with Qt 6" ON)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")

if (${APNG_QT6})
  set(APNG_QT_VERSION 6)
else ()
  set(APNG_QT_VERSION 5)
  include(Qt5Plugin)
endif ()

find_package(Qt${APNG_QT_VERSION} REQUIRED COMPONENTS Core Gui)

add_subdirectory(src)

if(APNG_TESTS)
  find_package(Qt${APNG_QT_VERSION} REQUIRED COMPONENTS Test)
  add_subdirectory(tests)
endif()

if(APNG_TESTS)
  find_package(Qt${APNG_QT_VERSION} REQUIRED COMPONENTS Widgets)
  add_subdirectory(examples)
endif()
