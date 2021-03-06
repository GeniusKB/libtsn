project(libtsn)

cmake_minimum_required(VERSION 2.8.3)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/CMake/Modules")

add_subdirectory(json-cpp)

find_package(OAuth REQUIRED)

option (BUILD_SHARED_LIBS "Build shared libraries." On)

set(OAuthClient_SRC ${CMAKE_CURRENT_LIST_DIR}/src/OAuthClient.cpp)
set(OAuthClient_DEP ${OAUTH_LIBRARY})

set(objectFactory_SRC ${CMAKE_CURRENT_LIST_DIR}/src/objectFactory.cpp)
set(objectFactory_DEP jsoncpp)

include_directories(${JSONCPP_SOURCE_DIR}/include)

add_library(tsn ${OAuthClient_SRC} ${objectFactory_SRC})
target_link_libraries(tsn ${OAuthClient_DEP} ${objectFactory_DEP})