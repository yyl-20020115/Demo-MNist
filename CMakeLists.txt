cmake_minimum_required(VERSION 3.10)
project(MNISTDemo LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_DEBUG_POSTFIX "d")
# FOR MFC
set(CMAKE_WIN32_MFC ON)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/Debug)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/Release)
 
add_definitions(-D_AFXDLL)
add_definitions("-DUNICODE" "-D_UNICODE")

SET(CMAKE_MFC_FLAG 2)

set(CMAKE_RC_COMPILER "rc.exe")
set_source_files_properties(MNist.rc PROPERTIES LANGUAGE RC)

add_executable(
    ${PROJECT_NAME} 
    CntrItem.cpp
    DlgBackpropParameters.cpp
    DlgCharacterImage.cpp
    DlgNeuralNet.cpp
    DlgResizeHelper.cpp
    DlgTesting.cpp
    DlgTestingParameters.cpp
    MainFrm.cpp
    MNistDoc.cpp
    MNistView.cpp
    NeuralNetwork.cpp
    Preferences.cpp
    StdAfx.cpp
    TabbedControlPanel.cpp
    WndCharImage.cpp
    WndGraphicMSE.cpp
    WndNeuronViewer.cpp
    MNist.cpp
    MNist.rc
)

target_link_libraries(
    ${PROJECT_NAME} 
    ${MFC_LIBRARIES})

set_target_properties(
    ${PROJECT_NAME}
    PROPERTIES LINK_FLAGS "/SUBSYSTEM:WINDOWS"
)
set_property(TARGET ${PROJECT_NAME} PROPERTY UNICODE ON)

    