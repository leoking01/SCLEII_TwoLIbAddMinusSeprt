

# 生成可执行文件
add_executable(mymathapp  mymathApp.cc)
target_link_directories(mymathapp PRIVATE ${CMAKE_BINARY_DIR})
target_link_libraries(mymathapp mymath)
target_include_directories(mymathapp PRIVATE ${CMAKE_SOURCE_DIR}/MyMath/include)

# 将库文件，可执行文件，头文件安装到指定目录
install(TARGETS      mymathapp
#    EXPORT MyMathTargets
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    RUNTIME DESTINATION bin
    PUBLIC_HEADER DESTINATION include
)

