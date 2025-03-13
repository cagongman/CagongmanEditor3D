cmake_minimum_required(VERSION 3.19)
project(CagongmanEditor3D LANGUAGES CXX)

find_package(Qt6 6.5 REQUIRED COMPONENTS Core Widgets OpenGL)

qt_standard_project_setup()

qt_add_executable(CagongmanEditor3D
    WIN32 MACOSX_BUNDLE
    main.cpp
    mainwindow.cpp
    mainwindow.h
    mainwindow.ui
)

target_link_libraries(CagongmanEditor3D
    PRIVATE
        Qt::Core
        Qt::Widgets
        Qt6::OpenGL
)

include(GNUInstallDirs)

install(TARGETS CagongmanEditor3D
    BUNDLE  DESTINATION .
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
)

qt_generate_deploy_app_script(
    TARGET CagongmanEditor3D
    OUTPUT_SCRIPT deploy_script
    NO_UNSUPPORTED_PLATFORM_ERROR
)
install(SCRIPT ${deploy_script})
