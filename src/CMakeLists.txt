#the code below needs to be able to include the Safir SDK Core headers
include_directories(${SAFIR_SDK_CORE_INCLUDE_DIRS})

#we also need boost
FIND_PACKAGE(Boost COMPONENTS filesystem REQUIRED)
#include_directories(${Boost_INCLUDE_DIRS})
#link_directories(${Boost_LIBRARY_DIRS})

#Boost Asio strands can share the same implementation instance which means that hanging or long running operations can potentially block
#other strands. This symbol will make the first 193 strands unique and therefor in practice avoid any shared instances. 
ADD_DEFINITIONS(-DBOOST_ASIO_ENABLE_SEQUENTIAL_STRAND_ALLOCATION)

#use dynamic linking with boost
ADD_DEFINITIONS(-DBOOST_ALL_DYN_LINK)

#dont use autolinking with boost
ADD_DEFINITIONS(-DBOOST_ALL_NO_LIB)

#disable deprecated functionality that we don't want
ADD_DEFINITIONS(-DBOOST_FILESYSTEM_NO_DEPRECATED)
ADD_DEFINITIONS(-DBOOST_SYSTEM_NO_DEPRECATED)

#we want to use boost::chrono instead of std::chrono and date_time for threads and asio
ADD_DEFINITIONS(-DBOOST_ASIO_DISABLE_STD_CHRONO)
ADD_DEFINITIONS(-DBOOST_THREAD_DONT_USE_DATETIME)

#Make Boost.Chrono header-only
ADD_DEFINITIONS(-DBOOST_CHRONO_HEADER_ONLY)

#use Boost.Chrono v2
ADD_DEFINITIONS(-DBOOST_CHRONO_VERSION=2)

#Make sure we only use the header-only part of Boost.DateTime
ADD_DEFINITIONS(-DBOOST_DATE_TIME_NO_LIB)



#load macros for building dotnet stuff with cmake
include(${SAFIR_SDK_CORE_DOTNET_SETTINGS})
include(${SAFIR_SDK_CORE_JAVA_SETTINGS})

set (CSHARP_LIBRARY_PATHS "${SAFIR_SDK_CORE_CSHARP_LIBRARY_PATH}")

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -pthread -std=c++11")

add_subdirectory(tank_engine/src)
add_subdirectory(tank_match_server/src)
add_subdirectory(tank_game_gui/src)
add_subdirectory(players)
