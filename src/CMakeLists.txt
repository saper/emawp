add_library(emawp-lib SHARED
	awp.c
)

set_target_properties(emawp-lib PROPERTIES
	OUTPUT_NAME "emawp"
	SOVERSION ${APP_VERSION_MAJOR}.${APP_VERSION_MINOR}
	PUBLIC_HEADER ${CMAKE_SOURCE_DIR}/include/emawp.h
)

install(TARGETS emawp-lib
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib
	PUBLIC_HEADER DESTINATION include
)

add_executable(emawp
	emawp-tool.c
)

target_link_libraries(emawp m emawp-lib)

install(TARGETS emawp
	RUNTIME DESTINATION bin
)

# vim: tabstop=4
