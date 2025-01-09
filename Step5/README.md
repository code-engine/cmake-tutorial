# Step 5

Adding:

`MathFunctions/CMakeLists.txt`

```cmake
set(installable_libs MathFunctions tutorial_compiler_flags)
if(TARGET SqrtLibrary)
  list(APPEND installable_libs SqrtLibrary)
endif()
install(TARGETS ${installable_libs} DESTINATION lib)
install(FILES MathFunctions.h DESTINATION include)
```

`CMakeLists.txt`

```cmake
install(TARGETS Tutorial DESTINATION bin)
install(FILES "${PROJECT_BINARY_DIR}/TutorialConfig.h" DESTINATION include)
```

Running:

```bash
cmake --install .
```

Will output:

```bash
-- Installing: /usr/local/lib/libMathFunctions.a
-- Installing: /usr/local/lib/libSqrtLibrary.a
-- Installing: /usr/local/include/MathFunctions.h
-- Installing: /usr/local/bin/Tutorial
-- Installing: /usr/local/include/TutorialConfig.h
```
