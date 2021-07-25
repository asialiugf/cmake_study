list(APPEND SRC1 Mysqrt.cxx) 
#list(APPEND SRC2 Addd.cxx
#        Subb.cpp
#) 

#list(APPEND SRC2 Addd.cxx)
#list(APPEND SRC2 Subb.cpp)

#add_subdirectory(hello bin)

#AUX_SOURCE_DIRECTORY(. SRC2)

set(SRC2 Addd.cxx
#${HELLOSRC}
#./hello/Subb.cpp
)

add_subdirectory(hello)
list(APPEND LIBB Subb)

add_library(LIB1 ${SRC1})
add_library(LIB2 ${SRC2})
target_link_libraries(LIB2 PUBLIC ${LIBB})

target_include_directories(LIB1
          INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
          )
