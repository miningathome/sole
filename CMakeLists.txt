cmake_minimum_required (VERSION 2.8)

project(sole CXX)

if(CMAKE_COMPILER_IS_GNUCXX)
	list(APPEND CMAKE_CXX_FLAGS "-std=c++11")
endif()

include(cmake/clean_slate.cmake)

if(MSVC)
	add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

set(HDR_PUBLIC sole.hpp)

# add_executable(sole sole.cpp main.cpp ${HDR_PUBLIC})
add_library(sole STATIC 
	sole.cpp
	${HDR_PUBLIC})

set_target_properties(sole PROPERTIES PUBLIC_HEADER "${HDR_PUBLIC}")

include_directories(${CMAKE_CURRENT_SOURCE_DIR})

install(TARGETS sole
	LIBRARY DESTINATION lib COMPONENT lib
	ARCHIVE DESTINATION lib COMPONENT lib
	RUNTIME DESTINATION bin COMPONENT bin
	PUBLIC_HEADER DESTINATION include COMPONENT dev)
