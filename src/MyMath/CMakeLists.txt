
# 如果想生成动态库，使用下面的语句
add_library(mymath SHARED  mymath.cc)
target_include_directories(mymath PRIVATE  ${CMAKE_SOURCE_DIR}/MyMath/include)
set_target_properties(mymath PROPERTIES PUBLIC_HEADER ${CMAKE_SOURCE_DIR}/MyMath/include/mymath.h)





#//---MyMath---------------------------------------------
# 写入库的版本信息

write_basic_package_version_file(
    MyMathConfigVersion.cmake
    VERSION ${PACKAGE_VERSION}
    COMPATIBILITY AnyNewerVersion
)

# 将库文件，可执行文件，头文件安装到指定目录
install(TARGETS mymath
    EXPORT MyMathTargets
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    RUNTIME DESTINATION bin
    PUBLIC_HEADER DESTINATION include
)

# 将库的相关信息输出为MyMathConfig.cmake，供find_package查找
install(EXPORT MyMathTargets
    FILE MyMathTargets.cmake
    NAMESPACE MyMath::
    DESTINATION lib/cmake/MyMath
)

configure_file( MyMathConfig.cmake.in  MyMath/MyMathConfig.cmake @ONLY)
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/MyMath/MyMathConfig.cmake"
    "${CMAKE_CURRENT_BINARY_DIR}/MyMathConfigVersion.cmake"
    DESTINATION lib/cmake/MyMath
)


message( "{mymath_INCLUDE_DIRS} = ${mymath_INCLUDE_DIRS}"  )
message( "{INTERFACE_INCLUDE_DIRECTORIES} = ${INTERFACE_INCLUDE_DIRECTORIES}"  )

