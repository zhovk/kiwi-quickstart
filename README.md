# KiwiQuickstart

KiwiQuickstart is a C++ project that demonstrates the setup of a simple application using modern C++ features and several popular libraries. It provides a foundation for creating applications that can leverage graphical and system-level components, unit testing, logging, and entity-component systems (ECS).

## Features

- **Modern C++ Setup**: The project is configured to use C++20, ensuring the use of the latest C++ features and optimizations.
- **External Libraries**:
  - **SFML**: Simple and Fast Multimedia Library (SFML) is used for 2D graphics, window management, and user input.
  - **Catch2**: A modern, C++-native unit testing framework to facilitate writing tests for your project.
  - **spdlog**: A fast, header-only logging library for efficient logging.
  - **flecs**: An Entity-Component-System (ECS) library for organizing the game/application architecture.

## Project Setup

1. **CMake-based build system**: The project uses CMake to manage the build process, which simplifies integration with IDEs and build tools. The minimum required CMake version is 3.10.

2. **Dependencies**: Dependencies are fetched using CMake's `FetchContent` module:
   - **SFML** (v3.0.0)
   - **Catch2** (v3.7.1)
   - **spdlog** (v1.15.0)
   - **flecs** (v4.0.3)

3. **Directory Structure**:
   - **`src/`**: Contains the C++ source files.
   - **`include/`**: Contains header files for the project.
   - **`bin/`**: Output directory for compiled executables.
   - **`lib/`**: Output directory for libraries.
   - **`external/`**: Directory for external dependencies.

4. **Compiling**:
   - The project is configured to build with C++20 and uses SFML for graphics handling and other multimedia components.
   - External dependencies are automatically fetched and linked during the build process.

5. **Logging**: The project integrates **spdlog** for efficient logging, providing a simple interface for logging messages.

6. **Testing**: **Catch2** is integrated to enable writing and running unit tests for the application.

## Building the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/zhovk/kiwi-quickstart.git
   ```

2. Create a build directory and run CMake:
   ```bash
   mkdir build
   cd build
   cmake ..
   ```

3. Build the project:
   ```bash
   cmake --build .
   ```

4. Run the application:
   ```bash
   ./bin/KiwiQuickstartExecutable
   ```

## License

This project is licensed under the MIT License.
