# Lua #

This is not the [official Lua repo][1]. This is a fork with CMake support.

## Embedding in CMake project ##

Example project structure:

```
project
|-CMakeLists.txt
|-main.c
|-lua
```

You would probably drop the `Lua` folder (or submodule) in an appropriate folder. For simplicity I decided not to do that.

```cmake
cmake_minimum_required(VERSION 2.4)

add_subdirectory(lua)

add_executable(my_project main.c)
target_link_libraries(my_project lua)
target_link_libraries(my_project lauxlib)
target_link_libraries(my_project lualib)
```

That's all. You can now use the Lua library like you want.

```c
#include <lua.h>
#include <lauxlib.h>
#include <lualib.h>

int main(void)
{
	lua_State* state = luaL_newstate();
	luaL_openlibs(state);
	luaL_dostring(state, "print('lua <3')");
	lua_close(state);
	return 0;
}

```

Output:
```
lua <3
```

[1]:https://github.com/lua/lua
