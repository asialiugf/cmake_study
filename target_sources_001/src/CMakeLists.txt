#add_library(automaton "")
#add_library(evolution "")

add_subdirectory(evolution)
add_subdirectory(initial)
add_subdirectory(io)
add_subdirectory(parser)
#include(${CMAKE_CURRENT_LIST_DIR}/evolution/CMakeLists.txt)
#include(${CMAKE_CURRENT_LIST_DIR}/initial/CMakeLists.txt)
#include(${CMAKE_CURRENT_LIST_DIR}/io/CMakeLists.txt)
#include(${CMAKE_CURRENT_LIST_DIR}/parser/CMakeLists.txt)

add_executable(mata "")

target_sources(mata
  PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}/main.cpp
  )

target_link_libraries(mata
  PRIVATE
    automaton
    conversion
  )

#message( "-------------------------: ${CMAKE_CURRENT_LIST_DIR}" )

target_include_directories(mata PUBLIC
                           ${CMAKE_CURRENT_LIST_DIR}
                           #${PROJECT_BINARY_DIR}
                           #${EXTRA1_INCLUDES}
                          )
