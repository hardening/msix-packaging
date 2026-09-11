# MSIX\src
# Copyright (C) 2017 Microsoft.  All rights reserved.
# See LICENSE file in the project root for full license information.

cmake_minimum_required(VERSION 3.8.0 FATAL_ERROR)

add_subdirectory(msix)
add_subdirectory(makemsix)
# MSIX_TESTS is declared in cmake/msix_options.cmake but was never actually consulted here,
# so -DMSIX_TESTS=OFF had no effect and the bundled catch2 (which doesn't compile against a
# modern glibc: MINSIGSTKSZ is no longer a compile-time constant) always broke a plain build.
if(MSIX_TESTS)
    add_subdirectory(test)
endif()
