list(APPEND SRC1 Mysqrt.cxx) 
#list(APPEND SRC2 Addd.cxx
#        Subb.cpp
#) 

#list(APPEND SRC2 Addd.cxx)
#list(APPEND SRC2 Subb.cpp)

set(SRC2 Addd.cxx
Subb.cpp)

add_library(LIB1 ${SRC1})
add_library(LIB2 ${SRC2})

#add_library(LIB1 Mysqrt.cxx)
#add_library(LIB2 Addd.cxx)
