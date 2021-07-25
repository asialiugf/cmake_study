cmake_minimum_required(VERSION 3.10)

message( STATUS "CMAKE_SOURCE_DIR: ${CMAKE_SOURCE_DIR}" )
message( STATUS "CMAKE_BINARY_DIR: ${CMAKE_BINARY_DIR}" )
message( STATUS "CMAKE_CURRENT_SOURCE_DIR: ${CMAKE_CURRENT_SOURCE_DIR}" )
message( STATUS "CMAKE_CURRENT_BINARY_DIR: ${CMAKE_CURRENT_BINARY_DIR}" )

if (EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/CMakeCache.txt" OR EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/CMakeFiles")
    message (FATAL_ERROR "!!!!!!!!!!!!!!!! source dir is dirty!!")
endif ()

if ( ${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_BINARY_DIR} )
    message( FATAL_ERROR "有问题：In-source builds not allowed! Create a build directory and run CMake from there. " )
endif()

foreach(policy
        CMP0023
        CMP0048 # CMake 3.0
        CMP0074 # CMake 3.12
        CMP0077
        CMP0079
    )
    if(POLICY ${policy})
        cmake_policy(SET ${policy} NEW)
    endif()
endforeach()


# set default policy
foreach(default_policy_var_name
        # make option() honor normal variables for BUILD_SHARED_LIBS:
        # - re2
        # - snappy
        CMAKE_POLICY_DEFAULT_CMP0077
        # Google Test from sources uses too old cmake, 2.6.x, and CMP0022 should
        # set, to avoid using deprecated LINK_INTERFACE_LIBRARIES(_<CONFIG>)? over
        # INTERFACE_LINK_LIBRARIES.
        CMAKE_POLICY_DEFAULT_CMP0022
    )
    set(${default_policy_var_name} NEW)
endforeach()

set(LINUX ON)
set(WIN32 OFF)


if(LINUX)
#if(NOT WIN32)
  string(ASCII 27 Esc)
  set(ColourReset "${Esc}[m")
  set(ColourBold  "${Esc}[1m")
  set(Red         "${Esc}[31m")
  set(Green       "${Esc}[32m")
  set(Yellow      "${Esc}[33m")
  set(Blue        "${Esc}[34m")
  set(Magenta     "${Esc}[35m")
  set(Cyan        "${Esc}[36m")
  set(White       "${Esc}[37m")
  set(BoldRed     "${Esc}[1;31m")
  set(BoldGreen   "${Esc}[1;32m")
  set(BoldYellow  "${Esc}[1;33m")
  set(BoldBlue    "${Esc}[1;34m")
  set(BoldMagenta "${Esc}[1;35m")
  set(BoldCyan    "${Esc}[1;36m")
  set(BoldWhite   "${Esc}[1;37m")
endif()

message("This is normal")
message("${Red}This is Red${ColourReset}")
message("${Green}This is Green${ColourReset}")
message("${Yellow}This is Yellow${ColourReset}")
message("${Blue}This is Blue${ColourReset}")
message("${Magenta}This is Magenta${ColourReset}")
message("${Cyan}This is Cyan${ColourReset}")
message("${White}This is White${ColourReset}")
message("${BoldRed}This is BoldRed${ColourReset}")
message("${BoldGreen}This is BoldGreen${ColourReset}")
message("${BoldYellow}This is BoldYellow${ColourReset}")
message("${BoldBlue}This is BoldBlue${ColourReset}")
message("${BoldMagenta}This is BoldMagenta${ColourReset}")
message("${BoldCyan}This is BoldCyan${ColourReset}")
message("${BoldWhite}This is BoldWhite\n\n${ColourReset}")




# set the project name and version
project(Tutorial VERSION 1.2.3.4)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# configure a header file to pass some of the CMake settings
# to the source code
configure_file(TutorialConfig.h.in TutorialConfig.h)

# add the executable
add_executable(Tutorial tutorial.cxx)

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(Tutorial PUBLIC "${PROJECT_BINARY_DIR}")
