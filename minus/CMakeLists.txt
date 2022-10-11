

# 如果想生成动态库，使用下面的语句
add_library(minus SHARED  minus_opera.cc)
target_include_directories(minus PRIVATE  ${CMAKE_SOURCE_DIR}/minus/include)
set_target_properties(minus PROPERTIES PUBLIC_HEADER ${CMAKE_SOURCE_DIR}/minus/include/minus_opera.h)




#//---minus---------------------------------------------
# 写入库的版本信息
#include(CMakePackageConfigHelpers)
write_basic_package_version_file(
    minusConfigVersion.cmake
    VERSION ${PACKAGE_VERSION}
    COMPATIBILITY AnyNewerVersion
)

# 将库文件，可执行文件，头文件安装到指定目录
install(TARGETS   minus
    EXPORT minusTargets
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    RUNTIME DESTINATION bin
    PUBLIC_HEADER DESTINATION include
)

# 将库的相关信息输出为MyMathConfig.cmake，供find_package查找
install(EXPORT minusTargets
    FILE minusTargets.cmake
    NAMESPACE minus::
    DESTINATION lib/cmake/minus
)

configure_file( minusConfig.cmake.in  minus/minusConfig.cmake @ONLY)
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/minus/minusConfig.cmake"
    "${CMAKE_CURRENT_BINARY_DIR}/minusConfigVersion.cmake"
    DESTINATION lib/cmake/minus
)
