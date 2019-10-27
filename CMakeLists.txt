cmake_minimum_required(VERSION 2.8.10)

set (INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src
                    /usr/local/include
					)
set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lib
            /usr/local/lib
	    /usr/lib/x86_64-linux-gnu
		${CMAKE_CURRENT_SOURCE_DIR}/)

add_compile_options(-std=c++11 -g)

include_directories(${INCLUDE_DIR})
link_directories(${LIB_DIR})

add_executable(epoller epoller.cpp test/epoller_test.cpp)
add_executable(channel channel.cpp test/channel_test.cpp)
add_executable(eventloop epoller.cpp channel.cpp eventloop.cpp test/eventloop_test.cpp)
add_executable(netutil netutil.cpp test/netutil_test.cpp)

target_link_libraries(epoller ${CMAKE_CURRENT_SOURCE_DIR}/libasynclogStaticLib.a  -lpthread)
target_link_libraries(channel ${CMAKE_CURRENT_SOURCE_DIR}/libasynclogStaticLib.a  -lpthread)
target_link_libraries(eventloop ${CMAKE_CURRENT_SOURCE_DIR}/libasynclogStaticLib.a  -lpthread)
target_link_libraries(netutil ${CMAKE_CURRENT_SOURCE_DIR}/libasynclogStaticLib.a  -lpthread)
