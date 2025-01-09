# Libraries and Linking

## Link library to executable

```cmake
target_link_libraries(<target> ... <item>... ...)
```

* The named `<target>` must have been created by a command such as `add_executable()` or `add_library()` and must not be an `ALIAS` target
* Each `<item>` may be:
  * A library target name
  * A full path to a library file
  * A plain library name
  * A link flag
  * A generator expression
  * A debug, optimized, or general keyword immediately followed by another `<item>`


Example

```cmake
target_link_libraries(Tutorial PUBLIC MathFunctions)
```

## Add a Library

```cmake
add_library(<name> [<type>] [EXCLUDE_FROM_ALL] <sources>...)
```

Add a library target called `<name>` to be built from the source files listed in the command invocation.

* The optional `<type>` specifies the type of library to be created:
  * `STATIC`: An archive of object files for use when linking other targets.
  * `SHARED`: A dynamic library that may be linked by other targets and loaded at runtime.
  * `MODULE`: A plugin that may not be linked by other targets, but may be dynamically loaded at runtime using dlopen-like functionality.

```cmake
add_library(MathFunctions MathFunctions.cxx mysqrt.cxx)
```

* Add a library to the project using the specified source files.
* Needs to be added to library `CMakeLists.txt`. It is the min requirement for a lib.
