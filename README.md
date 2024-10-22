# Duh

An application that walks recursively over the given directory and computes various information for every subdirectory down to the given depth. 
It is also possible to filter files by their extensions. It resembles the corresponding UNIX command-line utility (du).

## Functionality

This application provides the following command-line interface:

```
Usage: du [DIRECTORY] [-d|--depth DEPTH] [-e|--extension EXT] [-L]
  Directory usage info
Available options:
  -d,--depth DEPTH
  -e,--extension EXT
  -L
  -h,--help
Display an entry for all directories DEPTH
directories deep
Filter files by extension
Follow symlinks (OFF by default)
Show this help text
```

## Haskell stuff

The list of monads needed to build the application:
- `IO` for traversing over directories and determining file sizes
- `Reader` for accessing a configuration
- `State` for maintaining levels of subdirectories and accumulating file sizes
- `Writer` for logging the resulting information on traversed subdirectories.

## Modules

- `AppTypes` provides types used throughout the application.
- `AppRTWTST` describes our monad stack.
- `App` reexports definitions used in all other modules.
- `Utils` provides helpers to traverse a directory and acquire information about
files.
- `DirTree` builds a hierarchical view of a directory structure.
- `FileCount` counts files in the directories along the way.
- `DiskUsage` computes file space usage.
- `Main` provides the main function; it is also responsible for the user interface.
