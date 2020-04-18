cmake_minimum_required(VERSION 2.8)
project(qwt)

#--------------------------------------------------
# Setup Output directories
#--------------------------------------------------
SET (CMAKE_RUNTIME_OUTPUT_DIRECTORY
    ${PROJECT_BINARY_DIR}/bin CACHE PATH "Single Directory for all Executables."
)
SET (CMAKE_LIBRARY_OUTPUT_DIRECTORY
    ${PROJECT_BINARY_DIR}/bin CACHE PATH "Single Directory for all Libraries"
)
SET (CMAKE_ARCHIVE_OUTPUT_DIRECTORY
    ${PROJECT_BINARY_DIR}/bin CACHE PATH "Single Directory for all static libraries."
)

set(BUILD_SHARED_LIBS OFF)

find_package(OpenGL)
if (APPLE) 
  add_definitions(-DQWT_NO_OPENGL)
endif()

find_package(Qt5Core)
find_package(Qt5Widgets)
find_package(Qt5Gui)
find_package(Qt5Svg)
find_package(Qt5OpenGL)
find_package(Qt5Concurrent)
find_package(Qt5PrintSupport)

set(CMAKE_AUTOMOC ON)

include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}/class_includes
)

add_subdirectory(src)

option(QWT_BUILD_EXAMPLES ON)
if (QWT_BUILD_EXAMPLES)
  add_subdirectory(examples)
endif()
