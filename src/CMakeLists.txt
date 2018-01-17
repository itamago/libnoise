
SET(PROJECT_NAME libnoise)

INCLUDE_DIRECTORIES (.)
INCLUDE_DIRECTORIES (noise)

set(libSrcs ${libSrcs}
    noiseutils.h
    noiseutils.cpp
    noisegen.cpp
    latlon.cpp

    noise/model/line.h
    noise/model/plane.h
    noise/model/sphere.h
    noise/model/cylinder.h

    model/line.cpp
    model/plane.cpp
    model/sphere.cpp
    model/cylinder.cpp

    noise/module/abs.h
    noise/module/add.h
    noise/module/billow.h
    noise/module/blend.h
    noise/module/cache.h
    noise/module/checkerboard.h
    noise/module/clamp.h
    noise/module/const.h
    noise/module/curve.h
    noise/module/cylinders.h
    noise/module/displace.h
    noise/module/exponent.h
    noise/module/invert.h
    noise/module/max.h
    noise/module/min.h
    noise/module/modulebase.h
    noise/module/multiply.h
    noise/module/perlin.h
    noise/module/power.h
    noise/module/ridgedmulti.h
    noise/module/rotatepoint.h
    noise/module/scalebias.h
    noise/module/scalepoint.h
    noise/module/select.h
    noise/module/spheres.h
    noise/module/terrace.h
    noise/module/translatepoint.h
    noise/module/turbulence.h
    noise/module/voronoi.h

    module/abs.cpp
    module/add.cpp
    module/billow.cpp
    module/blend.cpp
    module/cache.cpp
    module/checkerboard.cpp
    module/clamp.cpp
    module/const.cpp
    module/curve.cpp
    module/cylinders.cpp
    module/displace.cpp
    module/exponent.cpp
    module/invert.cpp
    module/max.cpp
    module/min.cpp
    module/modulebase.cpp
    module/multiply.cpp
    module/perlin.cpp
    module/power.cpp
    module/ridgedmulti.cpp
    module/rotatepoint.cpp
    module/scalebias.cpp
    module/scalepoint.cpp
    module/select.cpp
    module/spheres.cpp
    module/terrace.cpp
    module/translatepoint.cpp
    module/turbulence.cpp
    module/voronoi.cpp
)

add_library( libnoise STATIC ${libSrcs} )

# this value is set in the root CMakeLists.txt
SET_TARGET_PROPERTIES( libnoise PROPERTIES LIBNOISE_VERSION ${LIBNOISE_VERSION} )

target_compile_definitions( libnoise PUBLIC NOISE_STATIC)

SET_TARGET_PROPERTIES( libnoise PROPERTIES OUTPUT_NAME "libnoise" )

# i would like to see more projects using these defaults
if (CMAKE_CXX_COMPILER_ID MATCHES "GNU")
  ADD_DEFINITIONS( "-Wall -ansi -pedantic -O3" )
endif()

# install include files into /usr/include
INSTALL( DIRECTORY "${PROJECT_SOURCE_DIR}/src/noise" DESTINATION
  "${CMAKE_INSTALL_PREFIX}/include" )

# install libraries into /lib
INSTALL( TARGETS libnoise DESTINATION "${CMAKE_INSTALL_PREFIX}/lib" )



