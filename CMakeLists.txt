project(Super_Peinture)
cmake_minimum_required(VERSION 2.8)
aux_source_directory(./src SOURCE_LIST)

set(HEADER_LIST
./include/pigment.h
./include/renderingwidget.h
./include/shader.h
./include/pipeline.h
./include/pipeline_cpu.h
./include/pipeline_gpu.h
./include/spectre.h
./include/light.h
./include/utils_kubelka
./include/configxml.h)

set(CMAKE_CXX_FLAGS "-std=c++11 -g -ggdb -O0 -Wall -Wextra")
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)


find_package(OpenGL REQUIRED)
find_package(Qt4 REQUIRED)

set(Qt4_LIBRARIES Qt4::QtGui Qt4::QtCore Qt4::QtOpenGL Qt4::QtXml)

#set(mixer_SOURCES ${CMAKE_SOURCE_DIR}/src/mainwindow.cpp)
#set(mixer_HEADERS ${CMAKE_SOURCE_DIR}/include/mainwindow.h)
#set(mixer_FORMS ${CMAKE_SOURCE_DIR}/src/mainwindow.ui)
#QT4_WRAP_CPP(mixer_HEADERS_MOCS ${mixer_HEADERS})
#QT4_WRAP_UI(mixer_FORMS_HEADERS ${mixer_FORMS})

QT4_WRAP_UI(UIS_HDRS
    ${CMAKE_SOURCE_DIR}/src/mixeur.ui)

include_directories(${OPENGL_INCLUDE_DIR})
include_directories(${Qt5Widgets_INCLUDE_DIRS})
include_directories(./include)

add_executable(${PROJECT_NAME} ${SOURCE_LIST} ${HEADER_LIST} ${UIS_HDRS})

target_link_libraries(${PROJECT_NAME} ${Qt4_LIBRARIES} ${OPENGL_LIBRARIES})

message(${SOURCE_LIST} ${HEADER_LIST})
