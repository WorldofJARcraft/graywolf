

#add_executable(mincut main.c output.c readcells.c ${CMAKE_SOURCE_DIR}/src/date/date.c)


add_library(ycadgraywolf SHARED assign.c buster.c cleanup.c colors.c deck.c dialog.c draw.c dset.c edcolors.c file.c getftime.c graph.c grid.c hash.c heap.c list.c log.c menus.c message.c mst.c mytime.c okmalloc.c path.c plot.c program.c project.c queue.c quicksort.c radixsort.c rand.c rbtree.c relpath.c set.c stat.c stats.c string.c system.c time.c timer.c trans.c wgraphics.c ydebug.c yreadpar.c )

target_link_libraries(ycadgraywolf ${X11_LIBRARIES})
target_link_libraries(ycadgraywolf m)

set_target_properties(ycadgraywolf PROPERTIES VERSION 1.0.0 SOVERSION 1)

if(NOGRAPHICS)
	message("Building ycadgraywolf without GUI")
	target_compile_definitions(ycadgraywolf INTERFACE NOGRAPHICS)
endif()

INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/include ${CMAKE_BINARY_DIR}/include ${X11_INCLUDE_DIR})

install(TARGETS ycadgraywolf DESTINATION ${CMAKE_INSTALL_LIBDIR})
