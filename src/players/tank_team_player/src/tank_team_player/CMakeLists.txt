FILE(GLOB sources *.cpp)
FILE(GLOB headers *.h)

ADD_EXECUTABLE(tank_team_player ${sources} ${headers})
target_link_libraries(tank_team_player PRIVATE safir_generated-Cwg-cpp ${SAFIR_SDK_CORE_LIBRARIES})

# INSTALL(TARGETS tank_team_player
#   RUNTIME DESTINATION ${SAFIR_RUNTIME}/bin
#   LIBRARY DESTINATION ${SAFIR_RUNTIME}/lib
#   ARCHIVE DESTINATION ${SAFIR_SDK}/lib)

# INSTALL_DEBUG_INFO(tank_team_player)
