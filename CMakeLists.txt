cmake_minimum_required(VERSION 3.4...3.18)
project(meshtaichi_patcher_core)

list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake/meshtaichi_patcher/")
list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake/recipes/")

# General CMake utils
include(meshtaichi_patcher_cpm_cache)

include(pybind11)
pybind11_add_module(meshtaichi_patcher_core src/main.cpp src/api.cpp src/mesh.cpp src/patcher_old.cpp src/csr.cpp src/cluster.cpp src/patcher.cpp)

# EXAMPLE_VERSION_INFO is defined by setup.py and passed into the C++ code as a
# define (VERSION_INFO) here.
target_compile_definitions(meshtaichi_patcher_core
                           PRIVATE VERSION_INFO=${EXAMPLE_VERSION_INFO})
