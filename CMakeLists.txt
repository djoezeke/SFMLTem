cmake_minimum_required(VERSION 3.16..4.1.1 FATAL_ERROR)

#--------------------------------------------------------------------
# Project and version.
#--------------------------------------------------------------------

set (TEMPLATE_VERSION_MAJOR 0)
set (TEMPLATE_VERSION_MINOR 1)
set (TEMPLATE_VERSION_PATCH 0)
set (TEMPLATE_VERSION_STRING ${TEMPLATE_VERSION_MAJOR}.${TEMPLATE_VERSION_MINOR}.${TEMPLATE_VERSION_PATCH})

project(SFMLTem
        VERSION ${TEMPLATE_VERSION_STRING} 
        DESCRIPTION "SFML Starter Template C/C++"
        HOMEPAGE_URL "https://github.com/djoezeke/SFMLTem"
        LANGUAGES  CXX
)

#--------------------------------------------------------------------
# Preparations depending on the specified build options  
#--------------------------------------------------------------------

if (CMAKE_CURRENT_SOURCE_DIR STREQUAL CMAKE_SOURCE_DIR)
  set(TEMPLATE_IS_TOP_LEVEL ON)
else()
  set(TEMPLATE_IS_TOP_LEVEL OFF)
endif()

#--------------------------------------------------------------------
# Configure variables   
#--------------------------------------------------------------------

set(TEMPLATE_EXE_NAME ${PROJECT_NAME} CACHE STRING "Base name of executable output name")
set(TEMPLATE_LIB_NAME ${PROJECT_NAME} CACHE STRING "Base name of library output name")

set(TEMPLATE_SOURCE_DIR "src" )
set(TEMPLATE_TESTS_DIR "tests")
set(TEMPLATE_INCLUDE_DIR "include")

set(TEMPLATE_SOURCE_FILES "src/main.cpp")

set(TEMPLATE_EXE_TARGET_NAME  ${TEMPLATE_EXE_NAME})
set(TEMPLATE_LIB_TARGET_NAME  ${TEMPLATE_LIB_NAME})

option(TEMPLATE_ENABLE_DEBUG "Enable debug build" OFF)
option(TEMPLATE_ENABLE_WARNINGS "Enable compiler warnings" OFF)
option(TEMPLATE_BUILD_TESTS "Build the ${PROJECT_NAME} test programs" ${TEMPLATE_IS_TOP_LEVEL})

# Set required C/C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_EXTENTIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

set(SFML_BUILD_TEST_SUITE OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(BUILD_SHARED_LIBS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

#--------------------------------------------------------------------
# Apply Microsoft C runtime library option
# This is here because it also applies to tests and examples
#--------------------------------------------------------------------
if (MSVC AND NOT USE_MSVC_RUNTIME_LIBRARY_DLL)
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Release>:Release>")
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()

#--------------------------------------------------------------------
# Configurations
#--------------------------------------------------------------------

# Default to build type "Release" unless debug is enabled
if(NOT CMAKE_BUILD_TYPE)
	if (NOT TEMPLATE_ENABLE_DEBUG)
		message(STATUS "No build type selected, default to Release")
		set(CMAKE_BUILD_TYPE "Release")
	else()
		message(STATUS "No build type selected but tests are being built, default to Debug")
		set(CMAKE_BUILD_TYPE "Debug")
	endif()
endif()

# Add compiler warnings
if(TEMPLATE_ENABLE_WARNINGS)
  if(MSVC)
    set(COMPILER_WARNINGS /WX /W4 /permissive-)
  elseif(CMAKE_CXX_COMPILER_ID MATCHES "(GNU|Clang)")
    set(COMPILER_WARNINGS -Werror -Wall -Wextra -Wpedantic -Wshadow -Wconversion -Wsign-conversion)
  endif()
endif()

# Output directories for a build tree
if(NOT DEFINED CMAKE_RUNTIME_OUTPUT_DIRECTORY)
  set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})
endif()

#--------------------------------------------------------------------
# Add Subdirectories
#--------------------------------------------------------------------


# Build the test apps   
if(TEMPLATE_BUILD_TESTS)
    include(CTest)
    enable_testing()
    add_subdirectory(${TEMPLATE_TESTS_DIR})

    # Set the unit test app project as the Visual Studio startup project
    # if the target compiler is some version of Microsoft Visual C++ and
    # if this project is the main project.
    if(MSVC AND CMAKE_CURRENT_SOURCE_DIR STREQUAL CMAKE_SOURCE_DIR)
        set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT "${PROJECT_NAME}Test")
    endif()
endif()

#--------------------------------------------------------------------
# Build targets
#--------------------------------------------------------------------

include_directories(".")

# Add executable
add_executable("${TEMPLATE_EXE_TARGET_NAME}" "src/main.cpp")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET "${TEMPLATE_EXE_TARGET_NAME}" PROPERTY CXX_STANDARD 20)
endif()

include(FetchContent)

# Configure SFML options before fetching (turn off examples/tests to keep fetch lightweight)
set(SFML_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(SFML_BUILD_TEST_SUITE OFF CACHE BOOL "" FORCE)
set(SFML_BUILD_DOC OFF CACHE BOOL "" FORCE)

FetchContent_Declare(
  SFML
  GIT_REPOSITORY https://github.com/SFML/SFML.git
  GIT_TAG 2.6.0
)
FetchContent_MakeAvailable(SFML)

# Link against the modern SFML CMake targets provided by the SFML project
if (DEFINED SFML_SOURCE_DIR)
  target_include_directories("${TEMPLATE_EXE_TARGET_NAME}" PRIVATE "${SFML_SOURCE_DIR}/include")
endif()

if (TARGET SFML::Graphics AND TARGET SFML::Window AND TARGET SFML::System)
  target_link_libraries("${TEMPLATE_EXE_TARGET_NAME}" PRIVATE SFML::Graphics SFML::Window SFML::System)
elseif (TARGET sfml-graphics AND TARGET sfml-window AND TARGET sfml-system)
  target_link_libraries("${TEMPLATE_EXE_TARGET_NAME}" PRIVATE sfml-graphics sfml-window sfml-system)
else()
  message(FATAL_ERROR "SFML CMake targets not found after FetchContent_MakeAvailable(SFML).")
endif()

# Preserve optional ImGui-SFML linkage if available
if (TARGET ImGui-SFML::ImGui-SFML)
  target_link_libraries("${TEMPLATE_EXE_TARGET_NAME}" PRIVATE ImGui-SFML::ImGui-SFML)
  if (DEFINED IMGUI_SFML_WARNINGS)
    target_compile_options("${TEMPLATE_EXE_TARGET_NAME}" PRIVATE ${IMGUI_SFML_WARNINGS})
  endif()
endif()
