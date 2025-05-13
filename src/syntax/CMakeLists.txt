

add_executable(syntax main.c output.c readcells.c ${CMAKE_SOURCE_DIR}/src/date/date.c)

target_link_libraries(syntax ycadgraywolf)
target_link_libraries(syntax ${X11_LIBRARIES})
target_link_libraries(syntax m)

if(YYDEBUG)
	target_compile_definitions(syntax INTERFACE YYDEBUG)
endif()

INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/include ${CMAKE_BINARY_DIR}/include .)

install(TARGETS syntax DESTINATION ${CMAKE_INSTALL_LIBEXECDIR}/graywolf/bin)
