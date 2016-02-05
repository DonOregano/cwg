FILE(GLOB ui *.ui)
FILE(GLOB sources *.cpp)
FILE(GLOB headers [!ui_]*.h)

find_package(Qt5Widgets REQUIRED)
find_package(Qt5Multimedia REQUIRED)

if (Qt5Widgets_VERSION VERSION_LESS "5.2.1")
  MESSAGE(WARNING "Qt versions below 5.2.1 may not play sounds correctly")
endif()

set(CMAKE_AUTOMOC ON)
QT5_WRAP_UI(ui_headers ${ui})
QT5_ADD_RESOURCES(qrc_src application.qrc)

ADD_EXECUTABLE(tank_game_gui WIN32 ${sources} ${ui_headers} ${moc_sources} ${qrc_src} ${headers})

TARGET_LINK_LIBRARIES(tank_game_gui safir_generated-Cwg-cpp ${SAFIR_SDK_CORE_LIBRARIES})

qt5_use_modules(tank_game_gui Widgets Multimedia)
QT5_WRAP_CPP(moc_sources ${headers} ${QT5_WRAP_CPP_OPTIONS})

# INSTALL(TARGETS tank_game_gui
#   RUNTIME DESTINATION ${SAFIR_RUNTIME}/bin
#   LIBRARY DESTINATION ${SAFIR_RUNTIME}/lib
#   ARCHIVE DESTINATION ${SAFIR_SDK}/lib)
# INSTALL_DEBUG_INFO(tank_game_gui)
