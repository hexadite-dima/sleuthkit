cmake_minimum_required(VERSION 3.5)

add_definitions(-DHAVE_TSK_LIBTSK_H)
add_definitions(-DHAVE_LIBZ)

set(cflags
    CMAKE_CXX_FLAGS
    CMAKE_CXX_FLAGS_DEBUG
    CMAKE_CXX_FLAGS_RELEASE
    CMAKE_C_FLAGS
    CMAKE_C_FLAGS_DEBUG
    CMAKE_C_FLAGS_RELEASE)
foreach(flags ${cflags})
	string(REPLACE "/MD" "/MT" ${flags} "${${flags}}")
endforeach()

include(base/CMakeLists.txt)
include(img/CMakeLists.txt)
include(vs/CMakeLists.txt)
include(fs/CMakeLists.txt)

install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/libtsk.h DESTINATION include/tsk)
