file(GLOB QWT_MML ${CMAKE_CURRENT_SRC_DIR} "*.cpp")

find_package(Qt5 REQUIRED QUIET COMPONENTS Core Widgets Gui OpenGL PrintSupport Svg Concurrent Xml)

add_library(qwtmml SHARED
    ${QWT_MML}
)

# important to have QWT_MOC_INCLUDE=1 for correct linking
target_compile_definitions(qwtmml PRIVATE QWT_DLL QT_STRICT_ITERATORS QWT_MOC_INCLUDE=1)

# cmake will do the moc generation for us
set_property(TARGET qwtmml PROPERTY AUTOMOC ON)

target_link_libraries(qwtmml PRIVATE
    qwt
    ${OPENGL_LIBRARIES}
    Qt5::Core
    Qt5::Widgets
    Qt5::Gui
    Qt5::OpenGL
    Qt5::PrintSupport
    Qt5::Svg
    Qt5::Concurrent
    Qt5::Xml
)
# important to have QWT_MOC_INCLUDE=1 for correct linking
target_compile_definitions(qwtmml PRIVATE QWT_DLL QT_STRICT_ITERATORS QWT_MOC_INCLUDE=1)

