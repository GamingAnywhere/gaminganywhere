cmake_minimum_required (VERSION 3.15)

project(${PROJECT_NAME}-client VERSION 0.0.1)

find_package(SDL2 CONFIG REQUIRED)
find_package(SDL2-ttf CONFIG REQUIRED)
find_package(live555 REQUIRED)

add_executable(${PROJECT_NAME}
	#src/generic_client.cpp
	#src/generic_client.hpp
	src/main.cpp
	src/minih264.cpp
	src/minih264.hpp
	src/minivp8.cpp
	src/minivp8.hpp
	src/qos_report.cpp
	src/qos_report.hpp
	src/rtsp_client.cpp
	src/rtsp_client.hpp
)
target_include_directories(${PROJECT_NAME} PUBLIC src)
target_link_libraries(${PROJECT_NAME}
	PRIVATE
		${CMAKE_PROJECT_NAME}::core
		SDL2::SDL2 
		SDL2::SDL2_ttf
		live555::liveMedia
		live555::Groupsock
		live555::BasicUsageEnvironment
		live555::UsageEnvironment
)
target_compile_definitions(${PROJECT_NAME} PRIVATE NOMINMAX SDL_MAIN_HANDLED)

