# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
#
cmake_minimum_required (VERSION 3.10)

project ("project_name")

# Include sub-projects.
add_definitions(-DDLOG_TIMESTAMP)
add_subdirectory (thirdparty/dlog)
add_definitions(-DDUTIL_ASSERT_DIALOG)
add_subdirectory (thirdparty/dutil)
# include_directories(SYSTEM thirdparty/abc/include)
# set(BUILD_EXAMPLES OFF CACHE BOOL "ex" FORCE)
# set(BUILD_EXAMPLE OFF CACHE BOOL "Build example" FORCE)

add_subdirectory (src)
if (WIN32)
  add_custom_target(
    copy-compile-commands ALL
    ${CMAKE_COMMAND} -E copy_if_different
    ${CMAKE_BINARY_DIR}/compile_commands.json
    ${CMAKE_CURRENT_LIST_DIR}
    )
endif ()
