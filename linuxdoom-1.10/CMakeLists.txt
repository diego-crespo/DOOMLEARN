# CMakeLists.txt

cmake_minimum_required(VERSION 3.0)
project(LinuxDoom)

# Set the compiler
set(CMAKE_C_COMPILER gcc)  # You can change this to g++ if needed

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-unused-but-set-variable")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-unused-but-set-variable")

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-pointer-to-int-cast")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-pointer-to-int-cast")

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-unused-const-variable")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-unused-const-variable")
# Compiler flags
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g -Wall -DNORMALUNIX -DLINUX")  # Add any other flags you need

# Source files
file(GLOB SOURCES "*.c")

# Output directory for object files
set(OBJ_DIR linux)
file(MAKE_DIRECTORY ${CMAKE_BINARY_DIR}/${OBJ_DIR})

# Executable
add_executable(linuxxdoom ${SOURCES})

# Set the output directory for the executable
set_target_properties(linuxxdoom PROPERTIES
        RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/${OBJ_DIR}
)

# Additional libraries
target_link_libraries(linuxxdoom
        -L/usr/X11R6/lib
        -lXext
        -lX11
        -lnsl
        -lm
)

# Check if the "linux" folder exists, and create it if not
if (NOT EXISTS ${CMAKE_BINARY_DIR}/${OBJ_DIR})
    file(MAKE_DIRECTORY ${CMAKE_BINARY_DIR}/${OBJ_DIR})
endif()
