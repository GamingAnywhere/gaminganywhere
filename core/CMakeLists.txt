cmake_minimum_required (VERSION 3.15)

project(${PROJECT_NAME}-core VERSION 0.0.1)

set(INCLUDE inc/ga)

add_library(${PROJECT_NAME}
	${INCLUDE}/asource.hpp
	${INCLUDE}/avcodec.hpp
	${INCLUDE}/common.hpp
	${INCLUDE}/conf.hpp
	${INCLUDE}/confvar.hpp
	${INCLUDE}/controller.hpp
	${INCLUDE}/crc.hpp
	${INCLUDE}/ctrl_msg.hpp
	${INCLUDE}/dpipe.hpp
	${INCLUDE}/encoder_common.hpp
	${INCLUDE}/module.hpp
	${INCLUDE}/rtsp_conf.hpp
	${INCLUDE}/vconverter.hpp
	${INCLUDE}/vsource.hpp
	${INCLUDE}/win32.hpp

	src/asource.cpp
	src/avcodec.cpp
	src/common.cpp
	src/conf.cpp
	src/confvar.cpp
	src/controller.cpp
	src/crc.cpp
	src/ctrl_msg.cpp
	src/dpipe.cpp
	src/encoder_common.cpp
	src/libga.cpp
	src/module.cpp
	src/rtsp_conf.cpp
	src/vconverter.cpp
	src/vsource.cpp
)
target_compile_features(${PROJECT_NAME} PUBLIC cxx_std_17)
target_include_directories(${PROJECT_NAME} PUBLIC inc PRIVATE ${INCLUDE})
target_compile_definitions(${PROJECT_NAME} PUBLIC GA_LIB USE_GA_WIN32_MACRO)
set_target_properties(${PROJECT_NAME}
	PROPERTIES
		OUTPUT_NAME core
		MACOSX_RPATH  ON
		INSTALL_RPATH @executable_path
)

if(WIN32)
	target_link_libraries(${PROJECT_NAME} PRIVATE ws2_32)
	target_sources(${PROJECT_NAME} PRIVATE src/win32.cpp)
endif()

add_library(${CMAKE_PROJECT_NAME}::core ALIAS ${PROJECT_NAME})
