cmake_minimum_required (VERSION 3.15)

project(GamingAnywhere)

string(TOUPPER ${PROJECT_NAME} PROJECT_NAME_UPPER)

set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY BOTH)
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE BOTH)

option(${PROJECT_NAME_UPPER}_INSTALL_DEPENDENCIES "Install required libraries in package" ON)
option(${PROJECT_NAME_UPPER}_BUILD_TESTS "Build ${PROJECT_NAME} tests" OFF)

#find_package(SDL2			REQUIRED)
#find_package(SDL2_net	REQUIRED)
#find_package(SDL2_ttf	REQUIRED)
#find_package(freetype	REQUIRED)
#find_package(OpenSSL		QUIET)
find_package(Threads		REQUIRED)
#find_package(ffmpeg		REQUIRED)
#find_package(fmt			REQUIRED)
#find_package(jsoncpp		REQUIRED)
#find_package(live555		REQUIRED)
#find_package(spdlog		REQUIRED)

add_subdirectory(core)
#add_subdirectory(client)
#add_subdirectory(server)
