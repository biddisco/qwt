file(GLOB QWT_SRCS ${CMAKE_CURRENT_SRC_DIR} "*.cpp")

#qt5_wrap_cpp(QWT_MOC_SRCS ${QWT_SRCS} )

add_library(qwt
  ${QWT_SRCS}
  ${QWT_MOC_SRCS}
  ${QWT_HEADERS_MOC}
)

target_link_libraries(qwt ${OPENGL_LIBRARIES})
qt5_use_modules(qwt Core Widgets Gui OpenGL PrintSupport Svg Concurrent)
