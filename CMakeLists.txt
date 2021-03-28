# ------------------------------------------------------------------------------

# // - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
#
# Arcanoid2D.Root
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
set ( PROJECT_NAME "Arcanoid2D.Root" )

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
# OPTIONS & CONSTANTS
# =================================================================================

set ( CMAKE_INCLUDES_DIR "${CMAKE_SOURCE_DIR}/src/engine/cmake/" )

include ( "${CMAKE_INCLUDES_DIR}options.cmake" )

# =================================================================================
# CONFIGS
# =================================================================================

# Build-Type (debug, release)
include ( "${CMAKE_INCLUDES_DIR}buildType.cmake" )

# Platform
include ( "${CMAKE_INCLUDES_DIR}platform.cmake" )

# ABI
include ( "${CMAKE_INCLUDES_DIR}abi.cmake" )

# =================================================================================
# ENGINE
# =================================================================================

# zeroEngine
add_subdirectory ( "src/engine" )

# =================================================================================
# GAME
# =================================================================================

# CORE
add_subdirectory ( "src/game/core" )

# PLATFORM
#include ( "src/game/${PLATFORM}/build.cmake" )
add_subdirectory ( "src/game/${PLATFORM}" )

# =================================================================================
# LIBRARIES
# =================================================================================

# Audio

# Graphics

# Assets

# ------------------------------------------------------------------------------
