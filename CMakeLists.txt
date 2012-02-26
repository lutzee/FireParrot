# CMakeLists for CU-ARdrone

cmake_minimum_required (VERSION 2.6)
project (cuardrone)

set (DRONE_VERSION_MAJOR 0)
set (DRONE_VERSION_MINOR 1)

set(DRONE_HEADERS DroneConfig.h)
set(DRONE_SOURCES main.cpp)
source_group(cuardrone FILES ${DRONE_HEADERS} ${DRONE_SOURCES})

include_directories("${PROJECT_SOURCE_DIR}")

configure_file (
  "${PROJECT_SOURCE_DIR}/DroneConfig.h.in"
  "${PROJECT_SOURCE_DIR}/DroneConfig.h"
  )

add_executable(cuardrone ${DRONE_SOURCES} ${DRONE_HEADERS})