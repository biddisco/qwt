# get name of currect example dir
get_filename_component(NAME ${CMAKE_CURRENT_SOURCE_DIR} NAME)

# find all cpp files
file(GLOB SOURCE_FILES "*.cpp")

list(LENGTH SOURCE_FILES LEN)
if (${LEN} EQUAL 0)
  return()
endif()

# add exe target
add_executable(qwt_example_${NAME} ${SOURCE_FILES})

if ("${NAME}" MATCHES "mml")
  set(MML_LIB qwtmml)
endif()

# set libs 
target_link_libraries(qwt_example_${NAME} PUBLIC
    qwt
    ${MML_LIB}
    Qt5::Core
    Qt5::Widgets
    Qt5::Gui
    Qt5::OpenGL
    Qt5::PrintSupport
    Qt5::Svg
    Qt5::Concurrent
)
set_property(TARGET qwt_example_${NAME} PROPERTY AUTOMOC ON)
