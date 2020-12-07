cmake_minimum_required(VERSION 3.17)
project(detex C)

set(CMAKE_C_STANDARD 99)
set(DETEX_LIBRARY_TYPE STATIC)

include_directories(${PROJECT_SOURCE_DIR})
SET(LIBRARY_SOURCES
        bptc-tables.c
        bits.c
        convert.c
        decompress-bc.c
        decompress-bptc.c
        decompress-bptc-float.c
        decompress-etc.c
        decompress-eac.c
        decompress-rgtc.c
        division-tables.c
        file-info.c
        half-float.c
        hdr.c
        ktx.c
        misc.c
        raw.c
        texture.c)

if (${DETEX_LIBRARY_TYPE} EQUAL "SHARED")
    add_compile_definitions(DETEX_SHARED=1)
    add_library(detex SHARED ${LIBRARY_SOURCES})
else()
    add_library(detex STATIC ${LIBRARY_SOURCES})
endif()
