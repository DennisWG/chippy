project(chippy_test VERSION 0.1 LANGUAGES CXX)

add_executable(test_chippy
    dummy.cpp
)

if (CMAKE_BUILD_TYPE STREQUAL "Coverage")
    include(CodeCoverage)
    set_target_properties(
            test_chippy PROPERTIES
            COMPILE_FLAGS "-O0 -g -fprofile-arcs -ftest-coverage"
            LINK_FLAGS "-O0 -g -lgcov -fprofile-arcs -ftest-coverage"
    )

    SETUP_TARGET_FOR_COVERAGE(
        coverage
        test_chippy
        coverage_report
    )
endif()

target_link_libraries(test_chippy
    lib_chippy
)

add_test(test_chippy test_chippy)

install(TARGETS test_chippy
    RUNTIME  DESTINATION ${CMAKE_INSTALL_BINDIR}
)

export(TARGETS lib_chippy FILE chippy_config.cmake)