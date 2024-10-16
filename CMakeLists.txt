cmake_minimum_required(VERSION 3.16)

include(FetchContent)

set(target_name imgui_glfw_cmake)
file(GLOB imgui_headers "${YAE_imgui_sources_SOURCES}/*.h")
list(APPEND imgui_headers ${YAE_imgui_sources_SOURCES}/backends/imgui_impl_opengl3.h)
list(APPEND imgui_headers ${YAE_imgui_sources_SOURCES}/backends/imgui_impl_glfw.h)
file(GLOB imgui_sources "${YAE_imgui_sources_SOURCES}/*.cpp")
list(APPEND imgui_sources ${YAE_imgui_sources_SOURCES}/backends/imgui_impl_opengl3.cpp)
list(APPEND imgui_sources ${YAE_imgui_sources_SOURCES}/backends/imgui_impl_glfw.cpp)
add_library(${target_name} STATIC ${imgui_headers} ${imgui_sources})
target_include_directories(${target_name} PUBLIC ${YAE_imgui_sources_SOURCES})
target_link_libraries(${target_name} PUBLIC glfw)
