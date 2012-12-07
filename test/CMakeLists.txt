find_package( PythonInterp )
if( PYTHON_EXECUTABLE )

  add_test( NAME ReaderWriterTests
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMAND ${PYTHON_EXECUTABLE} runjsontests.py $<TARGET_FILE:jsontestrunner>
    )

  add_test( NAME UnitTests
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMAND ${PYTHON_EXECUTABLE} rununittests.py $<TARGET_FILE:test_lib_json>
    )

  find_program( VALGRIND_EXECUTABLE valgrind )
  if( EXISTS ${VALGRIND_EXECUTABLE} )
    add_test( NAME UnitTestsWithValgrind
      WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
      COMMAND ${PYTHON_EXECUTABLE} rununittests.py
        --valgrind
        --valgrind-path="${VALGRIND_EXECUTABLE}"
        $<TARGET_FILE:test_lib_json>
      )
  endif()

endif()
