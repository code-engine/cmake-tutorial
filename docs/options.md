# Options

## CLI Setting

Setting options on the command line

```bash
cmake ../ -DUSE_MYMATH=OFF
```

## In CMake Files

Use in CMake files

```cmake
option(USE_MYMATH "Use tutorial provided math implementation" ON)

if (USE_MYMATH)
  target_compile_definitions(MathFunctions PRIVATE "USE_MYMATH")
  add_library(SqrtLibrary STATIC mysqrt.cxx)
  target_link_libraries(MathFunctions PRIVATE SqrtLibrary)
endif()
```

## Target Compile Definitions

The target_compile_definitions can use a quoted or unquoted string:

```cmake
target_compile_definitions(MathFunctions PRIVATE USE_MYMATH)
target_compile_definitions(MathFunctions PRIVATE "USE_MYMATH")
```

## Use in Code

```cpp
#ifdef USE_MYMATH
  ...
#endif
```

## List options

```bash
cmake -LAH
```

* `-L`: list variables
* `-A`: include advanced variables.
* `-H`: include the help strings as `// My help` above each setting
