# Variables

## Project Variables

```cmake
${PROJECT_BINARY_DIR}
```

Full path to build directory for project. This is the binary directory of the most recent `project()` command.

```cmake
${PROJECT_SOURCE_DIR}
```

This is the source directory of the last call to the project() command made in the current directory scope or one of its parents. Note, it is not affected by calls to `project()` made within a child directory scope (i.e. from within a call to `add_subdirectory()` from the current scope).

## Version Variables

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
