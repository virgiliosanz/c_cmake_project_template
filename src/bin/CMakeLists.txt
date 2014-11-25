include_directories(../src/include)
link_directories(${CMAKE_CURRENT_BINARY_DIR}/../lib)

file(GLOB TESTS "*.c")
foreach(T_FILE ${TESTS})
  	get_filename_component(T_NAME ${T_FILE} NAME_WE)
	add_executable(${T_NAME} ${T_FILE})
	target_link_libraries(${T_NAME} core ${THIRDPARTY_LIBRARIES} -lpthread)
	add_test(NAME ${T_NAME} COMMAND ${T_NAME})
endforeach(T_FILE ${TESTS})

