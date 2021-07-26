cmake_minimum_required(VERSION 3.10)

# set the project name and version
project(Tutorial VERSION 1.0)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# should we use our own math functions
option(USE_MYMATH "Use tutorial provided math implementation" ON)

# configure a header file to pass some of the CMake settings
# to the source code
configure_file(TutorialConfig.h.in TutorialConfig.h)

# add the MathFunctions library
if(USE_MYMATH)
#  list(APPEND B LIB2)
#  list(APPEND EXTRA1_INCLUDES "${PROJECT_SOURCE_DIR}/MathFunctions"
#  list(APPEND EXTRA1_INCLUDES 
#          "${PROJECT_SOURCE_DIR}/MathFunctions/hello"
#)
  message("a")
endif()

add_library(LIB1 "")
#add_library(LIB2 "")
#add_library(Subb "")

add_subdirectory(MathFunctions bin)
add_subdirectory(MathFunctions/hello)

list(APPEND LIB11 LIB1 LIB2 Subb)

add_executable(xxx "")

target_sources(xxx
  PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}/tutorial.cxx
  )

#target_link_libraries(automata
#  PRIVATE
#    automaton
#    conversion
#  )

target_link_libraries(xxx PRIVATE ${LIB11})


target_include_directories(xxx PUBLIC
                           ${PROJECT_BINARY_DIR}
                           #${EXTRA1_INCLUDES}
                           )
