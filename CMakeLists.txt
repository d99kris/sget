# Project
cmake_minimum_required(VERSION 3.0...3.19 FATAL_ERROR)
project(sget NONE)

# Program
configure_file(sget ${CMAKE_CURRENT_BINARY_DIR}/sget COPYONLY)
install(PROGRAMS sget DESTINATION bin)

# Manuals
install(FILES sget.1 DESTINATION share/man/man1)

# Uninstall
add_custom_target(uninstall
  COMMAND "${CMAKE_COMMAND}" -E remove "${CMAKE_INSTALL_PREFIX}/bin/sget"
  COMMAND "${CMAKE_COMMAND}" -E remove "${CMAKE_INSTALL_PREFIX}/share/man/man1/sget.1"
)

# Test init
enable_testing()

# Test macro add_unit_test
macro (add_unit_test testname)
  configure_file(tests/${testname} ${CMAKE_CURRENT_BINARY_DIR}/${testname} COPYONLY)
  add_test(${testname} "${PROJECT_BINARY_DIR}/${testname}")
  set_tests_properties(${testname} PROPERTIES RUN_SERIAL TRUE)
endmacro (add_unit_test)

# Tests
add_unit_test(test001)
add_unit_test(test002)

