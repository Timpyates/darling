project(libmach-o)

cmake_minimum_required(VERSION 2.4.0)

if(COMMAND cmake_policy)
	cmake_policy(SET CMP0003 NEW)
endif(COMMAND cmake_policy)

set(mach-o_SRCS
	MachO.cpp
	FatMachO.cpp
	RebaseState.cpp
	BindState.cpp
	MachOImpl.cpp
)

add_library(mach-o SHARED ${mach-o_SRCS})
set_target_properties(mach-o PROPERTIES VERSION 1.0.0 SOVERSION 1.0)
set_target_properties(mach-o PROPERTIES COMPILE_FLAGS "-fvisibility=hidden")
target_link_libraries(mach-o -ldl -lpthread util)

install(TARGETS mach-o DESTINATION "lib${SUFFIX}/darling")

