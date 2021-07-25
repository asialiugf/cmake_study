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
  add_subdirectory(MathFunctions bin)
#  add_subdirectory(MathFunctions/hello)
  list(APPEND LIB1 LIB1 LIB2)
#  list(APPEND B LIB2)
#  list(APPEND EXTRA1_INCLUDES "${PROJECT_SOURCE_DIR}/MathFunctions"
#  list(APPEND EXTRA1_INCLUDES 
#          "${PROJECT_SOURCE_DIR}/MathFunctions/hello"
#)
endif()

# add the executable
add_executable(xxx tutorial.cxx)

target_link_libraries(xxx PRIVATE ${LIB1})
#target_link_libraries(xxx PRIVATE ${B})

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h

message( "LIBS: ${LIB1}" )
#message( "LIBS: ${B}" )
message( "INCS: ${EXTRA1_INCLUDES}" )
message( "INCS: ${EXTRA1_INCLUDES}" )
message( "OBJECT_BINARY_DIRUDES ：${PROJECT_BINARY_DIR}" )

target_include_directories(xxx PUBLIC
                           ${PROJECT_BINARY_DIR}
                           #${EXTRA1_INCLUDES}
                           )
