cmake_minimum_required(VERSION 2.4)

set(LUA_SOURCE_FILES
    lapi.c
    lcode.c
    lctype.c
    ldebug.c
    ldo.c
    ldump.c
    lfunc.c
    lgc.c
    llex.c
    lmem.c
    lobject.c
    lopcodes.c
    lparser.c
    lstate.c
    lstring.c
    ltable.c
    ltm.c
    lundump.c
    lvm.c
    lzio.c
	ltests.c
)

set(LAUXLIB_SOURCE_FILES
	lauxlib.c
)

set(LUALIB_SOURCE_FILES
    lbaselib.c
    lcorolib.c
    ldblib.c
    linit.c
    liolib.c
    lmathlib.c
    loadlib.c
    loslib.c
    lstrlib.c
    ltablib.c
	lutf8lib.c
)

add_library(lua ${LUA_SOURCE_FILES})
add_library(lauxlib ${LAUXLIB_SOURCE_FILES})
add_library(lualib ${LUALIB_SOURCE_FILES})

if(LUA_FLOORN2I=1)
	target_compile_definitions(lua PUBLIC LUA_FLOORN2I=1)
endif()

target_include_directories(lua PUBLIC lua ./)
target_include_directories(lauxlib PUBLIC lua ./)
target_include_directories(lualib PUBLIC lua ./)
target_link_libraries(lauxlib lua)
