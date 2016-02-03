file(GLOB headers *.h)
file(GLOB sources *.cpp)
add_executable(tank_player_grandmother ${sources} ${headers})

target_link_libraries(tank_player_grandmother PRIVATE safir_generated-Cwg-cpp ${SAFIR_SDK_CORE_LIBRARIES})

# install(TARGETS ${proj_name}
#         RUNTIME DESTINATION ${SAFIR_RUNTIME}/bin
#         LIBRARY DESTINATION ${SAFIR_RUNTIME}/lib
#         ARCHIVE DESTINATION ${SAFIR_SDK}/lib)

# INSTALL_DEBUG_INFO(${proj_name})

