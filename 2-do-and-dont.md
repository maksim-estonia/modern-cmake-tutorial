## Do's and Don'ts

### Minimum version

```
cmake_minimum_required(VERSION 3.1)
```

### Setting a project

```
project(MyProject VERSION 1.0
                  DESCRIPTION "Very nice project"
                  LANGUAGES CXX)
```

There is really nothing special about the project name. No targets are added at this point.

### Making an executable

A simple executable:

```
add_executable(one two.cpp three.h)
```

`one` is both the name of the executable file generated, and the name of the CMake target created (you'll hear a lot more about targets soon). The source file list comes next, and you can list as many as you'd like. CMake will only compile source file extensions. The header will be, for most intents and purposes, ignored; the only reason to list them is to get them to show up in IDEs. 

### Making a library

Making a library is done with `add_library`:

```
add_library(one STATIC two.cpp three.h)
```

You get to pick a type of library, STATIC, SHARED, or MODULE. If you leave this choice off, the value of BUILD_SHARED_LIBS will be used to pick between STATIC and SHARED.

Often you'll need to make a fictional target, that is, one where nothing needs to be compiled, for example, for a header-only library. That is called INTERFACE library, and is another choice; the only difference is it cannot be followed by filenames.

### Targets are your friend

Now we've specified a target, how do we add information about it? For example, maybe it needs an include directory:

```
target_include_directories(one PUBLIC include)
```

`target_include_directories` adds an include directory to a target. `PUBLIC` doesn't mean much for an executable; for a library it lets CMake know that any targets that link to this target must also need that include directory. Other options are `PRIVATE` (only affect the current target, not dependencies), and `INTERFACE` (only needed for dependencies).

We can then chain targets:

```
add_library(another STATIC another.cpp another.h)
target_link_libraries(another PUBLIC one)
```

`target_link_libraries` takes a target (`another`) and adds a dependency if a target is given. If no target of that name (`one`) exists, then it adds a link to a library called `one` on your path (hence the name of the command).