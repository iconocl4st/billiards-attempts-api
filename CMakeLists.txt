cmake_minimum_required(VERSION 3.13)
project(attempts_api)

set(CMAKE_CXX_STANDARD 17)
#set(CMAKE_VERBOSE_MAKEFILE on)

find_package(Threads REQUIRED)
find_package(Boost COMPONENTS system REQUIRED)

add_executable(
    attempts_api

    ${CMAKE_CURRENT_SOURCE_DIR}/src/attempts_api.cpp
)

target_include_directories(
    attempts_api

    PUBLIC
	${PROJECT_SOURCE_DIR}/src
	${PROJECT_SOURCE_DIR}/../billiards-common/src
	$ENV{REPOS}/billiards-common/src/
)


target_link_libraries(
    attempts_api

    Threads::Threads
	${Boost_SYSTEM_LIBRARY}
)

install(TARGETS attempts_api DESTINATION /app)
