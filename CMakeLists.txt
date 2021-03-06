CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

PROJECT(kazmath)

ENABLE_TESTING()
FIND_PACKAGE(PkgConfig REQUIRED)
SET(CMAKE_C_FLAGS "-std=c99")
#ADD_DEFINITIONS("-DUSE_DOUBLE_PRECISION")

SET(KAZMATH_HEADERS
    ${CMAKE_SOURCE_DIR}/kazmath/vec2.h
    ${CMAKE_SOURCE_DIR}/kazmath/vec3.h
    ${CMAKE_SOURCE_DIR}/kazmath/vec4.h
    ${CMAKE_SOURCE_DIR}/kazmath/mat4.h
    ${CMAKE_SOURCE_DIR}/kazmath/mat3.h
    ${CMAKE_SOURCE_DIR}/kazmath/ray2.h
    ${CMAKE_SOURCE_DIR}/kazmath/plane.h
    ${CMAKE_SOURCE_DIR}/kazmath/utility.h
    ${CMAKE_SOURCE_DIR}/kazmath/quaternion.h
    ${CMAKE_SOURCE_DIR}/kazmath/aabb.h
    ${CMAKE_SOURCE_DIR}/kazmath/kazmath.h
)

SET(GL_UTILS_HEADERS
    ${CMAKE_SOURCE_DIR}/kazmath/GL/mat4stack.h
    ${CMAKE_SOURCE_DIR}/kazmath/GL/matrix.h
)

SET(KAZMATH_SOURCES
    ${CMAKE_SOURCE_DIR}/kazmath/mat4.c
    ${CMAKE_SOURCE_DIR}/kazmath/mat3.c    
    ${CMAKE_SOURCE_DIR}/kazmath/plane.c      
    ${CMAKE_SOURCE_DIR}/kazmath/vec4.c
    ${CMAKE_SOURCE_DIR}/kazmath/quaternion.c 
    ${CMAKE_SOURCE_DIR}/kazmath/vec2.c
    ${CMAKE_SOURCE_DIR}/kazmath/vec3.c
    ${CMAKE_SOURCE_DIR}/kazmath/utility.c
    ${CMAKE_SOURCE_DIR}/kazmath/aabb.c
    ${CMAKE_SOURCE_DIR}/kazmath/ray2.c
    ${CMAKE_SOURCE_DIR}/kazmath/GL/mat4stack.c
    ${CMAKE_SOURCE_DIR}/kazmath/GL/matrix.c
)

ADD_SUBDIRECTORY(kazmath)
ADD_SUBDIRECTORY(tests)

ADD_SUBDIRECTORY(java)

SET(CPACK_PACKAGE_DEFAULT_LOCATION "/")
SET(CPACK_GENERATOR "RPM")
set(CPACK_PACKAGE_NAME "kazmath")
set(CPACK_PACKAGE_VENDOR "Kazade")
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "A simple 3D math library, designed for game development")
set(CPACK_PACKAGE_VERSION "0.5")
set(CPACK_PACKAGE_VERSION_MAJOR "0")
set(CPACK_PACKAGE_VERSION_MINOR "5")
set(CPACK_PACKAGE_VERSION_PATCH "0")
set(CPACK_PACKAGE_INSTALL_DIRECTORY "kazmath")

SET(CPACK_RPM_PACKAGE_NAME "kazmath-devel")
SET(CPACK_RPM_PACKAGE_RELEASE 1)
SET(CPACK_RPM_PACKAGE_LICENCE "Simplified BSD")
SET(CPACK_RPM_PACKAGE_GROUP "Development/Libraries")
SET(CPACK_RPM_PACKAGE_DESCRIPTION "
Kazmath is a 3D math library written in C. It's designed to be easy to use and understand.
The library contains math functions for 2D, 3D and 4D vectors. 3x3 and 4x4 matrices, quaternions, planes and axis-aligned boxes")

INCLUDE(CPack)
