file(GLOB QWT_SRCS ${CMAKE_CURRENT_SRC_DIR} "*.cpp")

#qt5_wrap_cpp(QWT_MOC_SRCS ${QWT_SRCS} )

add_library(qwt
  ${QWT_SRCS}
  ${QWT_MOC_SRCS}
  ${QWT_HEADERS_MOC}
)

target_link_libraries(qwt PRIVATE ${OPENGL_LIBRARIES})
target_link_libraries(qwt PUBLIC Qt5::Core Qt5::Widgets Qt5::Gui Qt5::OpenGL Qt5::PrintSupport Qt5::Svg Qt5::Concurrent)
