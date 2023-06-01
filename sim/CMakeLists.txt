# cmake_minimum_required(specify the minimum required version or throw fatal # error

cmake_minimum_required(VERSION 2.6 FATAL_ERROR)

#project name 
project(Simulation)

#load the geant4 package and the other required repos for UI and Vis
find_package(Geant4 REQUIRED ui_all vis_all)

include(${Geant4_USE_FILE})

file(GLOB sources ${PROJECT_SOURCE_DIR}/*.CC)

file(GLOB headers ${PROJECT_SOURCE_DIR}/*.hh)

add_executable(sim sim.cc ${sources} ${headers})

target_link_libraries(sim ${Geant4_LIBRARIES})

add_custom_target(Simulation DEPENDS sim)

