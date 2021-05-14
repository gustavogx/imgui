cmake_minimum_required(VERSION 3.10)
project(ImGui VERSION 0.0.1)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(IMGUI_DIR "${CMAKE_CURRENT_SOURCE_DIR}")

set(IMGUI_INC_PATH 
    "${IMGUI_DIR}"
    "${IMGUI_DIR}/backends"
)

set(IMGUI_IMPL
    "${IMGUI_DIR}/backends/imgui_impl_glfw.cpp"
    "${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp"
)

set(IMGUI_SOURCES
    "${IMGUI_DIR}/imgui.cpp"
    "${IMGUI_DIR}/imgui_demo.cpp"
    "${IMGUI_DIR}/imgui_draw.cpp"
    "${IMGUI_DIR}/imgui_widgets.cpp"
    "${IMGUI_IMPL}"
)

add_library(imgui
    STATIC
    "${IMGUI_SOURCES}"
)

target_include_directories(imgui 
    PUBLIC
    "${IMGUI_INC_PATH}"
)

target_link_libraries(imgui
    PUBLIC
    GL
    GLU
)