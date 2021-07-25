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

# 在./hello子目录中的CMakeLists.txt中，会生成一个 Subb 的库
add_subdirectory(hello)
# 要链接的库的清单 list名: LIBB，包含一个Subb的库
list(APPEND LIBB Subb)

add_library(LIB1 ${SRC1}) # 生成目标库 LIB1
add_library(LIB2 ${SRC2}) # 生成目标库 LIB2 需要编译 ${SRC2} 这些源文件
target_link_libraries(LIB2 PUBLIC ${LIBB}) # 目标库需要链接 ${LIBB}库

target_include_directories(LIB1
          PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}
          )

target_include_directories(LIB2
          INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
          )
