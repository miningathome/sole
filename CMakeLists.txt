cmake_minimum_required (VERSION 2.8)

project(sole CXX)

include(unifier/unifier.cmake)

# shared not supported atm
set(libtype "STATIC")

if(MSVC)
	add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

set(src "src/sole.cpp")
set(hdr_public "include/sole/sole.hpp")

# add_executable(sole sole.cpp main.cpp ${hdr_public})
add_library(sole ${libtype} ${src} ${hdr_public})

set_target_properties(sole PROPERTIES PUBLIC_HEADER "${hdr_public}")

#include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories("include/sole")

install(TARGETS sole
	RUNTIME DESTINATION bin
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib
	PUBLIC_HEADER DESTINATION include/sole)
