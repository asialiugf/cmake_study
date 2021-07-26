#               list(APPEND SRC1 Mysqrt.cxx) 
#list(APPEND SRC2 Addd.cxx
#        Subb.cpp
#) 

#list(APPEND SRC2 Addd.cxx)
#list(APPEND SRC2 Subb.cpp)

#add_subdirectory(hello bin)

#AUX_SOURCE_DIRECTORY(. SRC2)


target_sources(LIB1
  PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}/Mysqrt.cxx
# 以下两句加不加都一样，也就是说，这里没有必要指定 Mysqrt.h 因为下面一句 target_include_directories已经指定。
#  PUBLIC
#    ${CMAKE_CURRENT_LIST_DIR}/Mysqrt.h
  )



set(SRC2 Addd.cxx
#${HELLOSRC}
#./hello/Subb.cpp
)

#add_library(LIB1 ${SRC1})
add_library(LIB2 ${SRC2})

target_include_directories(LIB1
          INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
          )
