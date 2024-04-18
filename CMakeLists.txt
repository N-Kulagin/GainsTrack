cmake_minimum_required(VERSION 3.22.0)
project(GainsTrack VERSION 0.1.0 LANGUAGES C CXX)

include(CTest)
enable_testing()

if (${CMAKE_BUILD_TYPE} STREQUAL "Release")
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/../GainsTrack/bin/Release")
else()
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/../GainsTrack/bin/Debug")
endif()

if ( CMAKE_COMPILER_IS_GNUCC )
    set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -Wall -Wextra")
endif()
if ( MSVC )
    set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} /W4")
endif()


set(SOURCES 
    ./GainsTrack/src/main.cpp
    ./GainsTrack/src/sum.cpp
)

set(HEADERS 
    ./GainsTrack/include/sum.h
)



add_executable(${PROJECT_NAME} ${SOURCES} ${HEADERS})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)