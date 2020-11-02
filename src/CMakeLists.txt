# CMakeList.txt : CMake project, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.10)

set(CMAKE_CXX_STANDARD 17)

if (WIN32)
else ()
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -Wpedantic")
endif ()


set(COMMON_SOURCES
  main.cpp
  )

# Add source to this project's executable.
add_executable (${PROJECT_NAME} ${COMMON_SOURCES})
target_link_libraries(${PROJECT_NAME} dlog dutil)
