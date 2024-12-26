# Set minimum CMake version required
cmake_minimum_required(VERSION 3.10)

# Define project information
project(KiwiQuickstart
  VERSION 1.0.0
  LANGUAGES C CXX
)

# Set C and C++ standards
set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 20)

# Print project info for debugging/logging
message(STATUS "Configuring project: ${PROJECT_NAME} v${PROJECT_VERSION}")
message(STATUS "Using C++ standard: ${CMAKE_CXX_STANDARD}")
message(STATUS "Using C standard: ${CMAKE_C_STANDARD}")

# Fetch dependencies using FetchContent
include(FetchContent)

# Set the base directory for external dependencies
set(FETCHCONTENT_BASE_DIR "${CMAKE_BINARY_DIR}/external")
set(FETCHCONTENT_UPDATES_DISCONNECTED ON)

# Declare external dependencies

# SFML
FetchContent_Declare(
  SFML
  GIT_REPOSITORY https://github.com/SFML/SFML
  GIT_TAG 3.0.0
)
message(STATUS "Fetching SFML from GitHub...")

# Catch2 (unit testing framework)
FetchContent_Declare(
  Catch2
  GIT_REPOSITORY https://github.com/catchorg/Catch2
  GIT_TAG v3.7.1
)
message(STATUS "Fetching Catch2 from GitHub...")

# spdlog (logging library)
FetchContent_Declare(
  spdlog
  GIT_REPOSITORY https://github.com/gabime/spdlog
  GIT_TAG v1.15.0
)
message(STATUS "Fetching spdlog from GitHub...")

# flecs (entity-component-system library)
FetchContent_Declare(
  flecs
  GIT_REPOSITORY https://github.com/SanderMertens/flecs
  GIT_TAG v4.0.3
)
message(STATUS "Fetching flecs from GitHub...")

# Make external dependencies available
FetchContent_MakeAvailable(flecs spdlog Catch2 SFML)

# Define source files and create the executable
file(GLOB_RECURSE KiwiQuickstart_SRCS "src/*.cpp")

# Create the executable first
add_executable(KiwiQuickstartExecutable ${KiwiQuickstart_SRCS})

# Now specify the include directories
target_include_directories(
  KiwiQuickstartExecutable
  PUBLIC "${PROJECT_SOURCE_DIR}/include"
  PRIVATE "${PROJECT_BINARY_DIR}/external"
)

# Link external dependencies to the executable
target_link_libraries(KiwiQuickstartExecutable PRIVATE spdlog::spdlog)

# Ensure C++20 (or higher) is enabled for SFML
target_compile_features(KiwiQuickstartExecutable PRIVATE cxx_std_20)

# Print final setup message
message(STATUS "CMake configuration complete. Building project...")
