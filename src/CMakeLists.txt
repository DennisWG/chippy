project(chippy_lib VERSION 0.1 LANGUAGES CXX)

add_library(lib_chippy
	dummy.cpp
)

target_include_directories(lib_chippy
    PUBLIC
	    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/../include>
	    $<INSTALL_INTERFACE:../include>
)

target_compile_features(lib_chippy
    PUBLIC cxx_std_17
)

install(TARGETS lib_chippy EXPORT chippy_config
    ARCHIVE  DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY  DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME  DESTINATION ${CMAKE_INSTALL_BINDIR}
)
install(DIRECTORY ../include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})

install(EXPORT chippy_config DESTINATION share/MyLibrary/cmake)

export(TARGETS lib_chippy FILE chippy_config.cmake)