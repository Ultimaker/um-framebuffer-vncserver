cmake_minimum_required(VERSION 3.0.2)
project(um-framebuffer-vncserver)

add_subdirectory(framebuffer-vncserver)

install(PROGRAMS ${CMAKE_BINARY_DIR}/framebuffer-vncserver/framebuffer-vncserver
	DESTINATION bin)

if(EXISTS "${CMAKE_ROOT}/Modules/CPack.cmake")
	set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "Framebuffer vncserver")
	set(CPACK_PACKAGE_VENDOR "Ultimaker")
	set(CPACK_PACKAGE_CONTACT "Ultimaker <info@ultimaker.com>")
	if(NOT DEFINED CPACK_PACKAGE_VERSION)
		set(CPACK_PACKAGE_VERSION "9999.99.99")
	endif()
	if(NOT DEFINED CPACK_DEBIAN_PACKAGE_ARCHITECTURE)
		execute_process(COMMAND dpkg --print-architecture OUTPUT_VARIABLE CPACK_DEBIAN_PACKAGE_ARCHITECTURE OUTPUT_STRIP_TRAILING_WHITESPACE)
	endif()
	include(CPackConfig.cmake)
	include(CPack)
endif()
