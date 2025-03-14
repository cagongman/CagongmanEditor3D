cmake_minimum_required(VERSION 3.19)
project(CagongmanEditor3D LANGUAGES CXX)

set(Qt6_DIR "C:/Qt6/6.8.2/msvc2022_64/lib/cmake/Qt6")
set(CMAKE_PREFIX_PATH "C:/Qt6/6.8.2/msvc2022_64")

find_package(Qt6 6.5 REQUIRED COMPONENTS Core Gui Widgets OpenGL OpenGLWidgets)
find_package(OpenGL REQUIRED)

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
        Qt::Gui
        Qt::Widgets
        Qt::OpenGL
        Qt::OpenGLWidgets
        OpenGL::GL
        OpenGL::GLU
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
