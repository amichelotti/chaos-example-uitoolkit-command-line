
cmake_minimum_required(VERSION 2.6)
include($ENV{CHAOS_BUNDLE}/tools/project_template/CMakeChaos.txt)

SET(uicmdtest_exe_src main.cpp)

ADD_EXECUTABLE(ExampleUIToolkitCommandLine ${uicmdtest_exe_src})
TARGET_LINK_LIBRARIES(ExampleUIToolkitCommandLine chaos_uitoolkit chaos_common ${FrameworkLib})
IF(BUILD_FORCE_STATIC)
  SET(CMAKE_EXE_LINKER_FLAGS "-static -Wl,--whole-archive -lchaos_common -Wl,--no-whole-archive")
ELSE()
ENDIF()


INSTALL(TARGETS ExampleUIToolkitCommandLine
        DESTINATION "bin"
        PERMISSIONS OWNER_WRITE OWNER_READ OWNER_EXECUTE GROUP_READ GROUP_WRITE GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)
