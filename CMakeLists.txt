cmake_minimum_required(VERSION 3.14)
project(Granuvolver_C_plus_plus)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 99)

set(vst3sdk "D:/Code Projects/cpp-libraries/vst3sdk")
set(SDK_ROOT "${vst3sdk}")
set(SMTG_VSTGUI_ROOT "${vst3sdk}/vstgui4")

add_subdirectory(${vst3sdk} ${PROJECT_BINARY_DIR}/vst3sdk)
smtg_enable_vst3_sdk()

set(SMTG_CREATE_PLUGIN_LINK OFF)

smtg_add_vst3plugin(${PROJECT_NAME} 
    "include/plugcontroller.h"
    "include/plugids.h"
    "include/plugprocessor.h"
    "include/version.h"
    "src/plugfactory.cpp"
    "src/plugcontroller.cpp"
    "src/plugprocessor.cpp"
    "resource/plug.uidesc"
)

smtg_target_configure_version_file(${PROJECT_NAME})

smtg_target_add_plugin_resources(${PROJECT_NAME} 
    RESOURCES
        resource/plug.uidesc
        resource/background.png
        resource/animation_knob.png
        resource/background_2x.png
        resource/background_3x.png
        resource/animation_knob_3x.png
)

target_link_libraries(${PROJECT_NAME} PRIVATE base pluginterfaces sdk vstgui_support)


if(SMTG_MAC)
    #smtg_set_bundle(${PROJECT_NAME} INFOPLIST "${CMAKE_CURRENT_LIST_DIR}/resource/Info.plist" PREPROCESS)
elseif(SMTG_WIN)
   # target_sources(${PROJECT_NAME} PRIVATE resource/win32resource.rc)
    # set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT ${PROJECT_NAME})
endif()


