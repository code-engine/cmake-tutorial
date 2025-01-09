# Files and Directories

## Add a subdirectory

```cmake
add_subdirectory(MathFunctions)
```

* Copies a subdirectory into build directory.
* Expects subdirectory to contain a `CMakeLists.txt`.

## Include directories

Specifies include directories to use when compiling a given target.

```cmake
target_include_directories(<target> [SYSTEM] [AFTER|BEFORE]
  <INTERFACE|PUBLIC|PRIVATE> [items1...]
  [<INTERFACE|PUBLIC|PRIVATE> [items2...] ...])
```

### Links

https://cmake.org/cmake/help/latest/command/target_include_directories.html

### Example

```cmake
target_include_directories(Tutorial PUBLIC "${PROJECT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}/MathFunctions")
```

## Configure File

```cmake
configure_file(TutorialConfig.h.in TutorialConfig.h)
```

* Copy file and apply transformations to it.
