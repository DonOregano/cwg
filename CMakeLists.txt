cmake_minimum_required(VERSION 2.8.12)

PROJECT(cwg C CXX) #FindQt needs C

find_package(SafirSDKCore REQUIRED)

option(LASER "Enable the laser weapon" On)
option(SMOKE "Enable smoke" On)
option(REDEEMER "Enable redeemer" On)

if (NOT LASER)
  add_definitions(-DNOLASER)
endif()

if (NOT SMOKE)
  add_definitions(-DNOSMOKE)
endif()

if (NOT REDEEMER)
  add_definitions(-DNOREDEEMER)
endif()

add_subdirectory(tank_dou)


add_subdirectory(src)
