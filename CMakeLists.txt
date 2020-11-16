project(LastTrainHome)
cmake_minimum_required(VERSION 3.17)

find_package(PkgConfig)
pkg_check_modules(LTH REQUIRED glfw3 glew openal)

add_library(json SHARED json/json.c)
add_library(miniz SHARED miniz/miniz.c)
add_library(stb SHARED stb/stb_vorbis.c)

add_executable(
    LastTrainHome
    app.cpp audio.cpp entity.cpp
    font.cpp gfx.cpp lighting.cpp
    loader.cpp main.cpp sprite.cpp
    str.cpp things.cpp
)
target_link_libraries(LastTrainHome PRIVATE stb json miniz ${LTH_LIBRARIES})
target_include_directories(LastTrainHome PRIVATE ${LTH_INCLUDE_DIRS})
