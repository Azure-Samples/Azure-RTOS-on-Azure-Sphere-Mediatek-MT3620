#  Copyright (c) Microsoft Corporation. All rights reserved.
#  Licensed under the MIT License.

cmake_minimum_required (VERSION 3.8)
#set(CMAKE_TRY_COMPILE_TARGET_TYPE "STATIC_LIBRARY")
project (demo_threadx C ASM)

SET(CMAKE_ASM_FLAGS "-mcpu=cortex-m4")

azsphere_configure_tools(TOOLS_REVISION "20.04")
azsphere_configure_api(TARGET_API_SET "6")

ADD_COMPILE_DEFINITIONS(OSAI_BARE_METAL)
ADD_LINK_OPTIONS(-specs=nano.specs -specs=nosys.specs)

# Create executable
add_executable (${PROJECT_NAME} 
    ./demo_threadx/demo_threadx.c 
    ./demo_threadx/rtcoremain.c
    ./demo_threadx/tx_initialize_low_level.S)

add_subdirectory(MT3620_lib)

set(THREADX_ARCH "cortex_m4")
set(THREADX_TOOLCHAIN "gnu")
add_subdirectory(threadx)

target_link_libraries(${PROJECT_NAME} mt3620_lib MT3620_M4_Driver MT3620_M4_BSP)
target_link_libraries(${PROJECT_NAME} azrtos::threadx)

set_target_properties (${PROJECT_NAME} PROPERTIES LINK_DEPENDS ${PROJECT_SOURCE_DIR}/linker.ld)

# Add MakeImage post-build command
# include ("${AZURE_SPHERE_MAKE_IMAGE_FILE}")

azsphere_target_add_image_package(${PROJECT_NAME})

