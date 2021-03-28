# ------------------------------------------------------------------------------

# // - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
#
# Arcanoid2D.Windows
#
# License: see "LICENSE" file.
#
# // - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

# =================================================================================
# CMake Meta-Data
# =================================================================================

# CMake-Version
cmake_minimum_required ( VERSION 3.6 FATAL_ERROR ) # QT & Android

# =================================================================================
# OPTIONS
# =================================================================================

set ( CXX_VERSION 11 )

# =================================================================================
# PROJECT
# =================================================================================

# Project Name
set ( PROJECT_NAME "Arcanoid2D.Windows" )

# Project Version
set ( PROJECT_VERSION 0.0.1 )

# Project Description
set ( PROJECT_DESCRIPTION "2D Top-Down Game" )

# Configure Project
project ( ${PROJECT_NAME} VERSION ${PROJECT_VERSION} DESCRIPTION ${PROJECT_DESCRIPTION} LANGUAGES C CXX )

# C++ Version
set ( CMAKE_CXX_STANDARD ${CXX_VERSION} )
#set ( CMAKE_CXX_STANDARD 17 ) # Android stdlibc++ 14+
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

# Set Flags
# Flags:
# -fexceptions - enable C++ exceptions (GCC & MSVC), fcxx-exceptions (Clang);
set ( CMAKE_CXX_FLAGS "-fexceptions -fcxx-exceptions" ${CMAKE_CXX_FLAGS} )

# =================================================================================
# CONSTANTS
# =================================================================================

set ( SRC_PUBLIC_DIR "public/" )
set ( SRC_PRIVATE_DIR "private/" )

# =================================================================================
# HEADERS
# =================================================================================

set ( GAME_WINDOWS_HEADERS 
    "${SRC_PUBLIC_DIR}main.hpp" )

# =================================================================================
# SOURCES
# =================================================================================

set ( GAME_WINDOWS_SOURCES 
    "${SRC_PRIVATE_DIR}main.cpp" )

# =================================================================================
# RESOURCES
# =================================================================================

set ( EXECUTABLE_RESOURCES "${CMAKE_SOURCE_DIR}/res/windows/win_res.rc" )

# =================================================================================
# EXECUTABLE
# =================================================================================

if ( NOT DEFINED GAME )
    message ( FATA_ERROR "${PROJECT_NAME} - variable <GAME> is not defined. Its required to link executable with libraries" )
endif ( NOT DEFINED GAME )

if ( NOT DEFINED RUNTIME_OUTPUT_DIRECTORY )
    message ( FATA_ERROR "${PROJECT_NAME} - variable <RUNTIME_OUTPUT_DIRECTORY> is not defined" )
endif ( NOT DEFINED RUNTIME_OUTPUT_DIRECTORY )

# Add Executable Object
add_executable ( GAME ${GAME_WINDOWS_HEADERS} ${GAME_WINDOWS_SOURCES} ${EXECUTABLE_RESOURCES} )

# Configure Executable-Object
set_target_properties ( GAME PROPERTIES
    VERSION ${PROJECT_VERSION}
    RUNTIME_OUTPUT_NAME "Arcanoid2D"
    RUNTIME_OUTPUT_DIRECTORY "${RUNTIME_OUTPUT_DIRECTORY}" )

# Link Library
target_link_libraries ( GAME 
    Arcanoid2D.Core )

# Include Arcanoid2D.Core Headers
target_include_directories ( GAME PUBLIC "../core/public" )

# ------------------------------------------------------------------------------
