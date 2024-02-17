project(Imgui)
find_package(OpenGL REQUIRED)
file(GLOB_RECURSE imguiFiles CONFIGURE_DEPENDS "*.cpp" "*.h")
add_library(Imgui STATIC ${imguiFiles})
target_include_directories(Imgui PUBLIC "./" "backends")
set(linker "")
if (WIN32)
    set (linker "-limm32")
elseif (UNIX)
    set (linker "")
endif()

target_link_libraries(Imgui PRIVATE ${linker}
    PUBLIC
    glfw
    OpenGL::GL
)
