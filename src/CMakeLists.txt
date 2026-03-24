message(STATUS "CMAKE_CURRENT_SOURCE_DIR: ${CMAKE_CURRENT_SOURCE_DIR}")
set(SLSDETECTORCONTROL_TANGODS_SRC_FILES ${SRC_FILES}
    ${CMAKE_CURRENT_SOURCE_DIR}/ClassFactory.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/SlsDetectorControl.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/SlsDetectorControlClass.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/SlsDetectorControlStateMachine.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/SlsDetectorControlDynAttrUtils.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp)
add_executable(SlsDetectorControl ${SLSDETECTORCONTROL_TANGODS_SRC_FILES})
target_link_libraries(SlsDetectorControl slsDetectorShared Tango::Tango)
install(TARGETS SlsDetectorControl DESTINATION bin)
