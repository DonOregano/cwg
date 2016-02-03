
#TODO:foreach(flag ${MYFLAGS})
#  message("Adding define for ${flag}")
#  add_definitions(-D${flag})
#endforeach()

FILE(GLOB sources *.cpp)
FILE(GLOB headers *.h)

ADD_EXECUTABLE(tank_engine ${sources} ${headers})

target_link_libraries(tank_engine PRIVATE safir_generated-Cwg-cpp ${SAFIR_SDK_CORE_LIBRARIES})

#INSTALL(TARGETS tank_engine
#  RUNTIME DESTINATION ${SAFIR_RUNTIME}/bin
#  LIBRARY DESTINATION ${SAFIR_RUNTIME}/lib
#  ARCHIVE DESTINATION ${SAFIR_SDK}/lib)

#INSTALL_DEBUG_INFO(tank_engine)
