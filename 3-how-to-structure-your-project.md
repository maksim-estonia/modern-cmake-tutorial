## How to structure your project

This is what your files should look like when you start if your project is called `project`, with a library called `lib`, and a executable called `app`:

```
- project
    - CMakeLists.txt
    - cmake
        - FindSomeLib.cmake
        - something_else.cmake
    - include
        - project
            - lib.hpp
    - src
        - CMakeLists.txt
        - lib.hpp
    - apps
        - CMakeLists.txt
        - app.cpp
    - tests
        - CMakeLists.txt
        - testlib.cpp
    - docs
        - CMakeLists.txt
    - extern
        - googletest
```

Use `add_subdirectory` to add a subdirectory containing a `CMakeLists.txt`.

