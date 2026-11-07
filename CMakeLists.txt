cmake_minimum_required(VERSION 3.13)

project(wiiuse-bte-lwbt
	LANGUAGES C ASM
)

if(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
	set(CMAKE_INSTALL_PREFIX "${DEVKITPRO}/libogc" CACHE PATH "" FORCE)
endif()

include(GNUInstallDirs)

set(CMAKE_INSTALL_LIBDIR "${CMAKE_INSTALL_LIBDIR}/${CATNIP_PRESET}")

add_library(wiiuse_bte_lwbt_inc INTERFACE)

target_include_directories(wiiuse_bte_lwbt_inc INTERFACE
	${CATNIP_BUILD_DIR}
	gc
	gc/bte
	gc/wiiuse
)

macro(wiiuse_bte_lwbt_install_lib target)
	install(
		TARGETS ${target}
		ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
	)
endmacro()

add_subdirectory(lwbt)
add_subdirectory(wiiuse)

install(
	FILES LICENSE
	DESTINATION ${CMAKE_INSTALL_PREFIX}
)

install(
	DIRECTORY ${PROJECT_SOURCE_DIR}/gc/
	DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
	FILES_MATCHING
		PATTERN "*.h"
		PATTERN "*.hpp"
		PATTERN "*.inc"
)
