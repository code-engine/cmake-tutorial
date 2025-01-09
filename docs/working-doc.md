# CMake Current Working Doc

## Add target include to library code

```cmake
target_include_directories(MathFunctions INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})
```

* This defines that the current source directory will need to be included for consuming projects.
* INTERFACE here means that consumers will need this, but the producer does not.

### Remove list with appends

The following is missing from step 2 and is removed in step 3:

```cmake
list(APPEND EXTRA_INCLUDES "${PROJECT_SOURCE_DIR}/MathFunctions")
target_include_directories(Tutorial PUBLIC "${PROJECT_BINARY_DIR}" ${EXTRA_INCLUDES})
```

### List

https://cmake.org/cmake/help/latest/command/list.html

```cmake
list(APPEND <list> [<element>...])
```

Appends elements to the list. If no variable named `<list>` exists in the current scope its value is treated as empty and the elements are appended to that empty list.
