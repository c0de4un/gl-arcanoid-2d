# ------------------------------------------------------------------------------

# // - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
#
# Arcanoid2D.Core
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
set ( PROJECT_NAME "Arcanoid2D.Core" )

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

set ( GAME_CORE_HEADERS 
    "${SRC_PUBLIC_DIR}game/ArcanoidGame.hpp" )

# =================================================================================
# SOURCES
# =================================================================================

set ( GAME_CORE_SOURCES 
    "${SRC_PRIVATE_DIR}game/ArcanoidGame.cpp" )

# =================================================================================
# LIBRARY
# =================================================================================

# Create STATIC Library-Object
add_library ( Arcanoid2D.Core ${GAME_CORE_HEADERS} ${GAME_CORE_SOURCES} )

# ------------------------------------------------------------------------------
