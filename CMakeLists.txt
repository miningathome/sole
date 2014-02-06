cmake_minimum_required (VERSION 2.8)

project(sole CXX)

include(cmake/clean_slate.cmake)

if (MSVC)
	add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

set(HDR_PUBLIC sole.hpp)

add_library(sole STATIC 
	sole.cpp
	${HDR_PUBLIC})

set_target_properties(sole PROPERTIES PUBLIC_HEADER "${HDR_PUBLIC}")

install(TARGETS sole
	LIBRARY DESTINATION lib COMPONENT lib
	ARCHIVE DESTINATION lib COMPONENT lib
	PUBLIC_HEADER DESTINATION include COMPONENT dev)