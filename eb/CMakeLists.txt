CMAKE_MINIMUM_REQUIRED(VERSION 2.8.7)
PROJECT(eb C)

SET(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH}
    ${CMAKE_SOURCE_DIR}/../cmake/modules)

FIND_PACKAGE(Libevent REQUIRED core)
FIND_PACKAGE(ZLIB REQUIRED)

SET(INCLUDES ${LIBEVENT_INCLUDE_DIRS} ${ZLIB_INCLUDE_DIRS})

SET(LIBS ${LIBEVENT_LIBRARIES} ${ZLIB_LIBRARIES})

SET(SOURCES src/main.c)

INCLUDE_DIRECTORIES(${INCLUDES})
ADD_EXECUTABLE(eb ${SOURCES})

TARGET_LINK_LIBRARIES(eb ${LIBS})

INSTALL(TARGETS eb
    RUNTIME DESTINATION bin
)