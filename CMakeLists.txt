
cmake_minimum_required(VERSION 3.0)

SET ( LIBNOISE_VERSION "1.0.0-cmake" )

OPTION(BUILD_LIBNOISE_DOCUMENTATION "Create doxygen documentation for developers" OFF)
OPTION(BUILD_LIBNOISE_EXAMPLES "Build libnoise examples" OFF)

ADD_SUBDIRECTORY(src)

IF (BUILD_LIBNOISE_EXAMPLES)
    ADD_SUBDIRECTORY(examples)
ENDIF()

ADD_SUBDIRECTORY(doc)
