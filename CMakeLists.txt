cmake_minimum_required(VERSION 3.14)
project(Granuvolver_C_plus_plus CXX)

include(FetchContent)

FetchContent_Declare(
    vst3sdk
    GIT_REPOSITORY https://github.com/steinbergmedia/vst3sdk.git
    GIT_TAG v3.7.2_build_28
    GIT_SHALLOW    ON
    GIT_SUBMODULES base cmake pluginterfaces public.sdk vstgui4
)

FetchContent_MakeAvailable(vst3sdk)

smtg_add_vst3plugin(${PROJECT_NAME}
    "src/conv.cpp"
    "src/conv.h"
    "src/granuvolve.cpp"
    "src/granuvolve.h"
    ${vst3sdk_SOURCE_DIR}
)

target_link_libraries(${PROJECT_NAME} PRIVATE base sdk vstgui_support)