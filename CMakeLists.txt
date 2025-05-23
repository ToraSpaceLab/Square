cmake_minimum_required(VERSION 3.24)
project(Square)

# set the output directory for built objects.
# This makes sure that the dynamic library goes into the build directory automatically.
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")

# This assumes the SDL source is available in vendored/SDL
add_subdirectory(vendor/SDL EXCLUDE_FROM_ALL)

# This assumes the SDL_image source is available in vendored/SDL_image
add_subdirectory(vendor/SDL_image EXCLUDE_FROM_ALL)

# Create your game executable target as usual
add_executable(Square WIN32 src/main.cpp)

# Link to the actual SDL3 library.
target_link_libraries(Square PRIVATE SDL3_image::SDL3_image SDL3::SDL3)