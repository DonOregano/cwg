
#foreach(flag ${MYFLAGS})
#  message("Adding define for ${flag}")
#  add_definitions(-D${flag})
#endforeach()

file(GLOB headers *.h)
file(GLOB sources *.cpp)

add_executable(tank_match_server ${sources} ${headers})
target_link_libraries(tank_match_server PRIVATE safir_generated-Cwg-cpp ${SAFIR_SDK_CORE_LIBRARIES} ${Boost_FILESYSTEM_LIBRARY})
# swre_interface_cpp dose_cpp logging_cpp)

# find_package(Boost COMPONENTS system chrono filesystem)

# if (NOT MSVC)
#     #enable c++11
#     set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")
#     target_link_libraries(${proj_name}
#                             swre_interface_cpp
#                             dose_cpp
#                             dots_generated-Consoden-cpp
#                             dots_generated-Safir-cpp dots_cpp
#                             logging_cpp lluf_utils
#                             ${Boost_LIBRARIES})
# endif()

# install(TARGETS ${proj_name}
#         RUNTIME DESTINATION ${SAFIR_RUNTIME}/bin
#         LIBRARY DESTINATION ${SAFIR_RUNTIME}/lib
#         ARCHIVE DESTINATION ${SAFIR_SDK}/lib)

# INSTALL_DEBUG_INFO(${proj_name})
