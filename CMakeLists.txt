cmake_minimum_required(VERSION 3.9)
set( CMAKE_TOOLCHAIN_FILE "/content/vcpkg-export-20210601-110821/scripts/buildsystems/vcpkg.cmake" )

project (demo)

add_definitions(-std=c++11)
add_definitions("-Wall")

# =============================================================================
# make executable for testing purpose
# -----------------------------------------------------------------------------
add_executable(main
	main_executable.cpp
)

# Find Package
find_package( OpenCV REQUIRED )

if( OpenCV_FOUND )
  target_link_libraries( main ${OpenCV_LIBS} )
endif()
