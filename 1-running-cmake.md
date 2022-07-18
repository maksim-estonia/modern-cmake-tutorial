## Running CMake

### Building a project

The classic Cmake build procedure:

```
mkdir cmake-build
cd build
cmake ..
make
```

To install:

```
# from build directory
make install
```

### Picking a compiler

Selecting a compiler must be done on the first run in an empty directory. To pick Clang:

```
# from build directory
CC=clang CXX=clang++ cmake ..
```

That sets the environment variables in bash for CC and CXX, and CMake will respect those variables. 

### Picking a generator

You can build with a variety of tools; `make` is usually the default. To see all the tools CMake knows about on your system, run:

```
cmake --help
```

### Setting options

You set options in CMake with `-D`. You can see a list of options with `-L`, or a list with human-readable help with `-LH`. 

### Verbose and partial builds

### Options

CMake has support for cached options. A variable in CMake can be marked as "cached", which means it will be written to the cache (a file called `CMakeCache.txt` in the build directory) when it is encountered. 

### Standard options

These are common CMake options to most packages:

- `-DCMAKE_BUILD_TYPE=`: pick from Release, RelWithDebInfo, Debug, or sometimes more.
- `-DCMAKE_INSTALL_PREFIX`: the location to install to. System install on Unix would often be `/usr/local` (the default), user directions are often `~/.local`, or you can pick a folder.
- `-DBUILD_SHARED_LIBS=`: You can set this ON or OFF to control the default for shared libraries.
- `-DBUILD_TESTING`: This is a common name for enabling tests, not all packages use it.

### Debugging your CMake files

The `--trace` option will print every line of CMake that is run.

