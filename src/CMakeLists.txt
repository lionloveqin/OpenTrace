CMAKE_MINIMUM_REQUIRED (VERSION 2.6)
PROJECT (OpenTrace C CXX)

IF (NOT CMAKE_BUILD_TYPE)
   SET(CMAKE_BUILD_TYPE "Release")
ENDIF ()

SET (CMAKE_CXX_FLAGS 
   -g
   -DCHECK_PTHREAD_RETURN_VALUE
   -D_FILE_OFFSET_BITS=64
   -Wall
   -Werror
   -Wextra
   -Wconversion
   -Wno-unused-parameter
   -Wold-style-cast
   -Woverloaded-virtual
   -Wpointer-arith
   -Wshadow
   -Wwrite-strings
   -march=native
   -rdynamic
   )

SET (CMAKE_CXX_COMPILER "g++")
SET (CMAKE_CXX_FLAGS_DEBUG "-O0")
SET (CMAKE_CXX_FLAGS_RELEASE "-O2 -finline-limit=1000 -DNDEGUG")
SET (EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
SET (LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)

FIND_PACKAGE (BOOST REQUIRED)
FIND_PACKAGE (Protobuf)

ADD_SUBDIRECTORY(traceserver)
ADD_SUBDIRECTORY(traceclient)

