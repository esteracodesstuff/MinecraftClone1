cmake_minimum_required(VERSION 3.15)
project(MinecraftClone)

set(CMAKE_CXX_STANDARD 17)

if(MSVC)
    set(CMAKE_GENERATOR_PLATFORM x64)
endif()

# Include directories
include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw/include
    ${CMAKE_CURRENT_SOURCE_DIR}/libs/glad/include
    ${CMAKE_CURRENT_SOURCE_DIR}/libs/glm
)

# Add executable
add_executable(minecraft_clone 
    src/main.cpp
    libs/glad/src/glad.c  # Only Glad implementation, no OpenGL libs
)

# Link libraries - only GLFW and OpenGL
target_link_libraries(minecraft_clone 
    ${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw/lib-vc2022/glfw3.lib
    opengl32
)

file(COPY shaders DESTINATION ${CMAKE_BINARY_DIR})