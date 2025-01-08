# CMake Cheatsheet

## CMake Version

```cmake
cmake_minimum_required(VERSION 3.10)
```

## Project Name and Version

```cmake
project(Tutorial VERSION 1.1.1.1)
```

## C++ Standard

```cmake
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)
```

## Add a subdirectory

```cmake
add_subdirectory(MathFunctions)
```

* Copies a subdirectory into build directory.
* Expects subdirectory to contain a `CMakeLists.txt`.

## Link library to executable

```cmake
target_link_libraries(Tutorial PUBLIC MathFunctions)
```

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

## File Sets

* `PRIVATE` only used when building this target. All the include directories following `PRIVATE` will be used for the current target only, i.e., appending the directories to `INCLUDE_DIRECTORIES`.
* `INTERFACE` only used by things that consume this. All the include directories following `INTERFACE` will NOT be used for the current target but will be accessible for the other targets that have dependencies on the current target, i.e., appending the directories to `INTERFACE_INCLUDE_DIRECTORIES`.
* `PUBLIC` merges both of the above together. All the directories following PUBLIC will be used for the current target and the other targets that have dependencies on the current target, i.e., appending the directories to `INCLUDE_DIRECTORIES` and `INTERFACE_INCLUDE_DIRECTORIES`.

Descriptions derived from links below:

* https://leimao.github.io/blog/CMake-Public-Private-Interface/
* https://discourse.cmake.org/t/clarification-on-public-private-with-target-source-group/7845


## Variables

### Project Variables

```cmake
${PROJECT_BINARY_DIR}
```

Full path to build directory for project. This is the binary directory of the most recent `project()` command.

```cmake
${PROJECT_SOURCE_DIR}
```

This is the source directory of the last call to the project() command made in the current directory scope or one of its parents. Note, it is not affected by calls to `project()` made within a child directory scope (i.e. from within a call to `add_subdirectory()` from the current scope).

### Version Variables

Derived from the following command:

```cmake
project(Tutorial VERSION 1.1.1.1)
```

Format:

```
MAJOR.MINOR.PATCH.TWEAK
```

Use in a configure_file command:

```cmake
@{PROJECT_NAME}_VERSION_MAJOR@
@{PROJECT_NAME}_VERSION_MINOR@
@{PROJECT_NAME}_VERSION_PATCH@
@{PROJECT_NAME}_VERSION_TWEAK@
```

Example, assuming a project named `Tutorial`.

```cmake
@Tutorial_VERSION_MAJOR@
@Tutorial_VERSION_MINOR@
@Tutorial_VERSION_PATCH@
@Tutorial_VERSION_TWEAK@
```
