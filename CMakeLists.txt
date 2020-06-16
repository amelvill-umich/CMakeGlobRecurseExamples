cmake_minimum_required(VERSION 3.13)

# https://cmake.org/cmake/help/v3.13/command/file.html#filesystem

message("CMAKE_CURRENT_SOURCE_DIR is ${CMAKE_CURRENT_SOURCE_DIR}")

message("--------------------------------------------------------------------------")

#                   output var                              Directory to get paths relative to      Globbing expression
file(GLOB_RECURSE   IncludeDirRelToSourc        RELATIVE    "${CMAKE_CURRENT_SOURCE_DIR}"           "${CMAKE_CURRENT_SOURCE_DIR}/include/*")

# Note: https://stackoverflow.com/a/17666004
# If you "${list}" instead of ${list}, it will be printed with delimeters, so you'll get the much more readable "a;b;c;d" instead of "abcd"
message("IncludeDirRelToSource: ${IncludeDirRelToSourc}")

# does that first parameter even do anything? -- yeah it's the directory to get paths relative to, the line below just causes an error
#file(GLOB_RECURSE H_FILES_ONEPARAM RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}/include/*")
#message("Found h files (one param): ${H_FILES_ONEPARAM}")

message("--------------------------------------------------------------------------")

# This returns every single file in the current source directory (and recurses throuh subdirectories), not just stuff in the include/ directory
# Note that it's all relative to the include directory, e.g., this file is ../CMakeLists.txt
file(GLOB_RECURSE SourceFilesRelToInclude RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}/include" "*")
message("SourceFilesRelToInclude: ${SourceFilesRelToInclude}")

message("--------------------------------------------------------------------------")
# Finds all header files anywhere in the source directory (i.e., this directory)
file(GLOB_RECURSE AllHeaderFilesRelToSource RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}" "*.h")
message("AllHeaderFilesRelToSource: ${AllHeaderFilesRelToSource}")