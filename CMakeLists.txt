cmake_minimum_required(VERSION 3.5)

project(AR1100 LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Use the package PkgConfig to detect GTK+ headers/library files
FIND_PACKAGE(PkgConfig REQUIRED)
FIND_PACKAGE(GTK REQUIRED)
PKG_CHECK_MODULES(GTK REQUIRED gtk+-3.0)

add_executable(AR1100
  main.cpp AR1100.h AR1100.cpp
)

target_link_libraries(AR1100 ${GTK_LIBRARIES} usb-1.0)
target_include_directories(AR1100 PUBLIC ${GTK_INCLUDE_DIRS})
target_compile_options(AR1100 PUBLIC ${GTK_CFLAGS_OTHER})