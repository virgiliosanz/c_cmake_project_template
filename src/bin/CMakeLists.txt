include_directories(../src/include)
link_directories(${CMAKE_CURRENT_BINARY_DIR}/../lib)

file(GLOB EXES "*.c")
foreach(EXE_FILE ${EXES})
  	get_filename_component(EXE_NAME ${EXE_FILE} NAME_WE)
	add_executable(${EXE_NAME} ${EXE_FILE})
	target_link_libraries(${EXE_NAME} core ${THIRDPARTY_LIBRARIES} -lpthread)
endforeach(EXE_FILE ${EXES})

