# CMakeList.txt : CMake project for My-CMake-Demo-Build, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.20)
project("My-CMake-Demo-Build")

# create variables SDL2_path, SDL2_image_path holding the path to their folders
# !!! you need to change the paths to match the paths on your machine
set(SDL2_path "F:/Microsoft Visual Studio/SDL/SDL2-2.30.0")
set(SDL2_image_path "F:/Microsoft Visual Studio/SDL_image/SDL2_image-2.8.2")

# libraries to use
find_package(SDL2 REQUIRED PATHS "${SDL2_path}")
find_package(SDL2_image REQUIRED PATHS "${SDL2_image_path}")


# Add source files to this project's executable.
add_executable (${PROJECT_NAME} "main.cpp" "Game.h" "Game.cpp" "Shapes.h" "Shapes.cpp" "TextureManager.h" "TextureManager.cpp")

# link the libraries
target_link_libraries(${PROJECT_NAME} SDL2::SDL2 SDL2::SDL2main SDL2_image::SDL2_image)

# finds the .dll files and copies them to the build directory
# !!! you do not need to touch this
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD     
    COMMAND ${CMAKE_COMMAND} -E copy_if_different  
        "${SDL2_path}/lib/x64/SDL2.dll"      
        "${SDL2_image_path}/lib/x64/SDL2_image.dll"
        $<TARGET_FILE_DIR:${PROJECT_NAME}>   
    COMMAND ${CMAKE_COMMAND} -E copy_directory  
        "${CMAKE_CURRENT_SOURCE_DIR}/assets"
        $<TARGET_FILE_DIR:${PROJECT_NAME}>/assets )




if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.
