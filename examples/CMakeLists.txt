#
# to copy the stub CMakeLists into each example directory, use this
#
set(COPY_MSG "find . -maxdepth 1 -type d -not -name .git -not -name . -exec cp example_CMakeLists.txt.in {}/CMakeLists.txt \\\\;")

set(dirs
  controls       distrowatch    itemeditor     rasterview     simpleplot     stockchart
  animation      cpuplot        legends        realtime       sinusplot      
  barchart       curvdemo1      oscilloscope   refreshtest    spectrogram    sysinfo
  bode           dials          friedberg      radio          scatterplot    splineeditor   tvplot
)

include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}/../src
)

foreach(dir ${dirs})
  if (EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/${dir}/CMakeLists.txt)
    add_subdirectory(${dir})
  else()
    message("An example directory (${dir}) exists without a CMakeLists.txt file, use \n" 
      ${COPY_MSG} "\nfrom the examples dir to fix it")
  endif()
endforeach()

