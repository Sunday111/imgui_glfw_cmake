cmake_minimum_required(VERSION 3.16)

include(FetchContent)

set(target_name imgui_glfw_cmake)
file(GLOB imgui_headers "${YAE_CLONED_imgui_glfw_cmake}/*.h")
list(APPEND imgui_headers ${imgui_SOURCE_DIR}/backends/imgui_impl_opengl3.h)
list(APPEND imgui_headers ${imgui_SOURCE_DIR}/backends/imgui_impl_glfw.h)
file(GLOB imgui_sources "${YAE_CLONED_imgui_glfw_cmake}/*.cpp")
list(APPEND imgui_sources ${imgui_SOURCE_DIR}/backends/imgui_impl_opengl3.cpp)
list(APPEND imgui_sources ${imgui_SOURCE_DIR}/backends/imgui_impl_glfw.cpp)
add_library(${target_name} STATIC ${imgui_headers} ${imgui_sources})
target_include_directories(${target_name} PUBLIC ${imgui_SOURCE_DIR})
target_link_libraries(${target_name} PUBLIC glfw)
