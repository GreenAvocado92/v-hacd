# Copyright 2017 The LevelDB Authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file. See the AUTHORS file for names of contributors.

cmake_minimum_required(VERSION 3.10)
# Keep the version below in sync with the one in db.h
project(main VERSION 1.23.0 LANGUAGES C CXX)


# This project requires C++11.
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_BUILD_TYPE "Release")

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

find_package(CGAL REQUIRED COMPONENTS)
include_directories(${CGAL_INCLUDE_DIRS})

file(GLOB SRC ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp)
message(STATUS ${SRC})
add_executable(${PROJECT_NAME} ${SRC})

target_include_directories(${PROJECT_NAME} PUBLIC "../include")
# target_link_libraries(${PROJECT_NAME} ${PCL_LIBRARIES})
target_link_libraries(${PROJECT_NAME} CGAL::CGAL)


# On Linux we need to add pthread to the link
if (WIN32)
else (WIN32)
	target_link_libraries(${PROJECT_NAME} pthread)
endif (WIN32)
