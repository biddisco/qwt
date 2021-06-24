#
# to copy the stub CMakeLists into each example directory, use this
#
set(COPY_MSG "find . -maxdepth 1 -type d -not -name .git -not -name . -exec cp example_CMakeLists.txt.in {}/CMakeLists.txt \\\\;")

MACRO(SUBDIRLIST result curdir)
  FILE(GLOB children RELATIVE ${curdir} ${curdir}/*)
  SET(dirlist "")
  FOREACH(child ${children})
    IF(IS_DIRECTORY ${curdir}/${child})
      LIST(APPEND dirlist ${child})
    ENDIF()
  ENDFOREACH()
  SET(${result} ${dirlist})
ENDMACRO()

SUBDIRLIST(SUBDIRS ${CMAKE_CURRENT_LIST_DIR})

include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}/../src
)

foreach(dir ${SUBDIRS})
  if (EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/${dir}/CMakeLists.txt)
    add_subdirectory(${dir})
  else()
    message("An example directory (${dir}) exists without a CMakeLists.txt file, use \n" 
      ${COPY_MSG} "\nfrom the examples dir to fix it")
  endif()
endforeach()

