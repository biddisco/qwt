# get name of currect example dir
get_filename_component(NAME ${CMAKE_CURRENT_SOURCE_DIR} NAME)

# find all cpp files
file(GLOB COMMON_SOURCE "*.cpp")

# add exe target
add_executable(${NAME} ${COMMON_SOURCE})

# set libs 
target_link_libraries(${NAME} qwt)
qt5_use_modules(${dir} Core Widgets Gui OpenGL PrintSupport Svg Concurrent)

