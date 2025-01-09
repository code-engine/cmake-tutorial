# Access Specifiers

## File Sets

* `PRIVATE` only used when building this target. All the include directories following `PRIVATE` will be used for the current target only, i.e., appending the directories to `INCLUDE_DIRECTORIES`.
* `INTERFACE` only used by things that consume this. All the include directories following `INTERFACE` will NOT be used for the current target but will be accessible for the other targets that have dependencies on the current target, i.e., appending the directories to `INTERFACE_INCLUDE_DIRECTORIES`.
* `PUBLIC` merges both of the above together. All the directories following PUBLIC will be used for the current target and the other targets that have dependencies on the current target, i.e., appending the directories to `INCLUDE_DIRECTORIES` and `INTERFACE_INCLUDE_DIRECTORIES`.

Descriptions derived from links below:

* https://leimao.github.io/blog/CMake-Public-Private-Interface/
* https://discourse.cmake.org/t/clarification-on-public-private-with-target-source-group/7845
