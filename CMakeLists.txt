
project(lua_bson C)
cmake_minimum_required(VERSION 2.8)

option(BUILD_SHARED_LIBS "Build shared libraries" ON)

set(SRC "bson.c")

# find lua
include_directories("${CMAKE_SOURCE_DIR}/lua-prebuilt/lua-5.3/include" "${CMAKE_SOURCE_DIR}/${LUA_LIB_DIR}")
link_directories("${CMAKE_SOURCE_DIR}/${LUA_LIB_DIR}")

if(WIN32)
	add_definitions(-DLUA_BUILD_AS_DLL)
endif()

add_library(libbson ${SRC})
target_link_libraries(libbson lua)
if(MSVC)
	add_definitions(-D_CRT_SECURE_NO_WARNINGS)
	target_link_libraries(libbson ws2_32)
endif()
set_target_properties(libbson PROPERTIES OUTPUT_NAME bson CLEAN_DIRECT_OUTPUT 1 )

if(IPHONEOS_DEPLOYMENT_TARGET)
	set_xcode_property(libbson IPHONEOS_DEPLOYMENT_TARGET ${IPHONEOS_DEPLOYMENT_TARGET})
endif()

# install
set(LUA_VDIR "5.3")
install(TARGETS libbson DESTINATION ${CMAKE_INSTALL_PREFIX}/lib/lua/${LUA_VDIR})


