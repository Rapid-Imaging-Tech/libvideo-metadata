# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

project(video-metadata)

set(CMAKE_C_STANDARD 99)

set(SRC_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src)
set(INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include)

add_library(
		video-metadata
		SHARED

		${SRC_DIR}/protobuf-c.c
		${SRC_DIR}/vmeta.pb-c.c
		${SRC_DIR}/systimetools.c
		
		${SRC_DIR}/vmeta_frame.c
		${SRC_DIR}/vmeta_frame_proto.c
		${SRC_DIR}/vmeta_frame_v1.c
		${SRC_DIR}/vmeta_frame_v2.c
		${SRC_DIR}/vmeta_frame_v3.c
		${SRC_DIR}/vmeta_session.c
		${SRC_DIR}/vmeta_utils.c
)

target_include_directories(video-metadata PUBLIC  ${INCLUDE_DIR})
target_include_directories(video-metadata PRIVATE ${SRC_DIR})