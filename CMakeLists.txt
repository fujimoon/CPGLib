cmake_minimum_required(VERSION 3.0)
set(CMAKE_OSX_ARCHITECTURES x86_64;i386)

if (POLICY CMP0025)
  cmake_policy(SET CMP0025 NEW)
endif ()

set (CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "-std=c++11 ${CMAKE_CXX_FLAGS}")

project(MatsuokaEngine)

aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR} MAT_SOURCES)

#file(GLOB MAT_SOURCES "*.cpp *.c")

add_library(MatsuokaEngine STATIC ${MAT_SOURCES})

if (CMAKE_BUILD_TYPE STREQUAL "Debug")
	add_definitions(
		-DDEBUG
	)
	set(
		CMAKE_LIBRARY_OUTPUT_DIRECTORY
		../../build/x64/Debug
	)
else ()
	set(
		CMAKE_LIBRARY_OUTPUT_DIRECTORY
		../../build/x64/Release
	)
endif ()
