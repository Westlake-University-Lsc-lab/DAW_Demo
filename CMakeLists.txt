
cmake_minimum_required(VERSION 3.10)

# 设置项目名称
project(DAW_WXY C)
# 设置C标准
set(CMAKE_C_STANDARD 99)


# 设置编译标志以生成 32 位程序
# set(CMAKE_C_FLAGS "-m")
# set(CMAKE_CXX_FLAGS "-m32")
# set(CMAKE_EXE_LINKER_FLAGS "-m32")


# 添加头文件目录
include_directories(${CMAKE_SOURCE_DIR}/inc)
include_directories(/usr/include)

find_library(CAEN_LIB CAENDigitizer HINTS /usr/lib)
file(GLOB sources ${PROJECT_SOURCE_DIR}/src/*.c)
file(GLOB headers ${PROJECT_SOURCE_DIR}/inc/*.h)

file(GLOB caenlibs /usr/lib/*.so)
# 添加要编译的源文件
add_executable(DAW_WXY ${sources} ${headers})
target_link_libraries(DAW_WXY ${CAEN_LIB} ${caenlibs} m)


# 安装规则
# 安装后的操作

install(TARGETS DAW_WXY DESTINATION /home/wxy/local/bin)
install(CODE "execute_process(COMMAND chmod 777 /home/DAW_Demo/DAW_Config.txt)")


