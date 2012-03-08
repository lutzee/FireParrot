# CMakeLists for CU-ARdrone

cmake_minimum_required (VERSION 2.6)
project (cuardrone)

# Build the gamepad lib
add_subdirectory(gamepad)

link_directories (${cuardrone_BINARY_DIR}/gamepad) 

set(DRONE_VERSION_MAJOR 0)
set(DRONE_VERSION_MINOR 1)

set(DRONELIB_HEADERS DroneLib/ARDrone.h DroneLib/MemoryLibrary.h)
set(DRONELIB_SOURCES DroneLib/ARDrone.cpp)

set(DRONE_HEADERS   DroneConfig.h InputDevice.h Drone.h)
set(DRONE_SOURCES   main.cpp Drone.cpp)
source_group(cuardrone FILES    ${DRONE_HEADERS} ${DRONE_SOURCES}
                                ${DRONELIB_HEADERS} ${DRONELIB_SOURCES})

include_directories("${PROJECT_SOURCE_DIR}")

configure_file (
  "${PROJECT_SOURCE_DIR}/DroneConfig.h.in"
  "${PROJECT_SOURCE_DIR}/DroneConfig.h"
  )

add_executable(cuardrone    ${DRONE_SOURCES} ${DRONE_HEADERS}
                            ${DRONELIB_SOURCES} ${DRONELIB_HEADERS})

target_link_libraries(cuardrone gamepad commonc++ X11)