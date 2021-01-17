cmake_minimum_required(VERSION 3.12)
cmake_policy(SET CMP0048 NEW)

project(qwt)

cmake_policy(SET CMP0072 NEW)

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

find_package(Qt5 REQUIRED QUIET COMPONENTS Core Widgets Gui OpenGL PrintSupport Svg Concurrent)

include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}/classincludes
  ${CMAKE_CURRENT_SOURCE_DIR}/src
  ${CMAKE_CURRENT_SOURCE_DIR}/textengines/mathml
)

add_subdirectory(src)
add_subdirectory(textengines/mathml)

option(QWT_BUILD_EXAMPLES ON)
if (QWT_BUILD_EXAMPLES)
  add_subdirectory(examples)
endif()
