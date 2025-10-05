
# ImGui - Immediate Mode UI
set(IMGUI_DIR "${CMAKE_CURRENT_SOURCE_DIR}/imgui/")


set(IMGUI_SFML_FIND_SFML OFF)
set(IMGUI_SFML_IMGUI_DEMO OFF)
set(IMGUI_SFML_ENABLE_WARNINGS OFF)
set(IMGUI_SFML_USE_DEFAULT_CONFIG ON)

# ImGui-SFML
add_subdirectory(imgui-sfml)

# SFML - Simple and Fast Multimedia Library
set (SFML_STATIC_LIBRARIES TRUE)

add_subdirectory(sfml)
