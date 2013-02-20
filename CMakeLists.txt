cmake_minimum_required( VERSION 2.8 )

project( sfMod )

if( NOT CMAKE_BUILD_TYPE )
	set( CMAKE_BUILD_TYPE Release CACHE STRING "Choose the type of build (Debug or Release)" FORCE )
endif()

set( BUILD_SHARED false CACHE BOOL "Build a shared library." )

if( BUILD_SHARED )
	set( LIB_TYPE SHARED )
else()
	set( LIB_TYPE STATIC )
endif()

set( SFML_COMPONENTS ${SFML_COMPONENTS} AUDIO SYSTEM )

find_package( ModPlug REQUIRED )
find_package( SFML 2.0 REQUIRED COMPONENTS ${SFML_COMPONENTS} )

set( INC_DIR "include" )
set( SRC_DIR "src" )

set(
	SOURCES
	${INC_DIR}/sfMod.h
	${INC_DIR}/sfMod/Error.h
	${SRC_DIR}/sfMod/sfMod.cpp
)

include_directories( ${INC_DIR} )
include_directories( ${INC_DIR}/sfMod )

include_directories( ${ModPlug_INCLUDE_DIR} )
include_directories( ${SFML_INCLUDE_DIR} )

add_library( sfMod ${LIB_TYPE} ${SOURCES} )

target_link_libraries( sfMod ${ModPlug_LIBRARY} )
target_link_libraries( sfMod ${SFML_AUDIO_LIBRARY} )
target_link_libraries( sfMod ${SFML_SYSTEM_LIBRARY} )

if( BUILD_SHARED )
	set_target_properties( sfMod PROPERTIES DEBUG_POSTFIX -d )
else()
	set_target_properties( sfMod PROPERTIES DEBUG_POSTFIX -s-d )
	set_target_properties( sfMod PROPERTIES RELEASE_POSTFIX -s )
	set_target_properties( sfMod PROPERTIES MINSIZEREL_POSTFIX -s )
endif()

# Installing

install(
	DIRECTORY include
	DESTINATION .
)

install(
	FILES license.txt
	DESTINATION .
)

install(
	FILES readme.txt
	DESTINATION .
)

if(WIN32)
	install(
		TARGETS sfMod
		RUNTIME DESTINATION bin
		LIBRARY DESTINATION lib
		ARCHIVE DESTINATION lib
	)
else()
	install(
		TARGETS sfMod
		RUNTIME DESTINATION lib
		LIBRARY DESTINATION lib
		ARCHIVE DESTINATION lib
	)
endif()
