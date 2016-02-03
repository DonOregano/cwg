cmake_minimum_required(VERSION 2.8.12)

PROJECT(cwg C CXX) #FindQt needs C

find_package(SafirSDKCore REQUIRED)

add_subdirectory(tank_dou)


add_subdirectory(src)
