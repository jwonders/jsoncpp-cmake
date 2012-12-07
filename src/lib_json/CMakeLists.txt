set( json_SRCS
  json_reader.cpp
  json_value.cpp
  json_writer.cpp
  )
add_library( json ${json_SRCS} )
install( TARGETS json
  ARCHIVE DESTINATION lib COMPONENT Development
  LIBRARY DESTINATION lib COMPONENT RuntimeLibraries
  )
