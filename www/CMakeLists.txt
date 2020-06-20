foreach(FILE index.html main.shui require.js shellfish.pkg)
  configure_file(${FILE} ${CMAKE_CURRENT_BINARY_DIR} COPYONLY)
endforeach()
