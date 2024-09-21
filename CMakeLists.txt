cmake_minimum_required(VERSION 3.16)

include(FetchContent)

set(target_name imgui_glfw_cmake)
file(GLOB imgui_headers "${YAE_CLONED_imgui_sources}/*.h")
list(APPEND imgui_headers ${YAE_CLONED_imgui_sources}/backends/imgui_impl_opengl3.h)
list(APPEND imgui_headers ${YAE_CLONED_imgui_sources}/backends/imgui_impl_glfw.h)
file(GLOB imgui_sources "${YAE_CLONED_imgui_sources}/*.cpp")
list(APPEND imgui_sources ${YAE_CLONED_imgui_sources}/backends/imgui_impl_opengl3.cpp)
list(APPEND imgui_sources ${YAE_CLONED_imgui_sources}/backends/imgui_impl_glfw.cpp)
add_library(${target_name} STATIC ${imgui_headers} ${imgui_sources})
target_include_directories(${target_name} PUBLIC ${YAE_CLONED_imgui_sources})
target_link_libraries(${target_name} PUBLIC glfw)
