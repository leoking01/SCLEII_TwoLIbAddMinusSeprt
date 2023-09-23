cmake_minimum_required(VERSION 3.0)

#project( SCLEII_TwoLIbAddMinusSeprt VERSION 1.0)
project(SCLEII_TwoLIbAddMinusSeprt
        VERSION 1.0.0
        DESCRIPTION "Modern C++ Snippets"
        HOMEPAGE_URL "https://alandefreitas.github.io/moderncpp/"
        )




#######################################################
### CMake Functions                                 ###
#######################################################
# Put ./cmake directory in our include paths
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
# Include our custom cmake functions
include(cmake/functions.cmake)
# Include FetchContent scripts
include(FetchContent)

#######################################################
### Options                                         ###
#######################################################
set_debug_booleans()
set_master_project_booleans()
set_optimization_flags()

# What to build
option(BUILD_SNIPPETS "Build snippets" ON)
option(BUILD_EXAMPLES "Build examples" ON)
# How to build
option(BUILD_WITH_PEDANTIC_WARNINGS "Use pedantic warnings." ${DEBUG_MODE})
option(BUILD_WITH_SANITIZERS "Use pedantic warnings." ${DEBUG_MODE})
option(BUILD_WITH_EXCEPTIONS "Add compiler flags to use exceptions." ON)









IF (CMAKE_SYSTEM_NAME MATCHES "Linux")
ELSEIF (CMAKE_SYSTEM_NAME MATCHES "Windows")
ELSEIF (CMAKE_SYSTEM_NAME MATCHES "FreeBSD")
ELSE ()
    MESSAGE(STATUS "other platform: ${CMAKE_SYSTEM_NAME}")
ENDIF (CMAKE_SYSTEM_NAME MATCHES "Linux")


if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
    # using Clang
elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
    # using GCC
elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Intel")
    # using Intel C++
elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
    # using Visual Studio C++
endif()


#cmake.exe -G "MinGW Makefiles"


IF (CMAKE_SYSTEM_NAME MATCHES "Linux")
    MESSAGE(STATUS "current platform: Linux ")
ELSEIF (CMAKE_SYSTEM_NAME MATCHES "Windows")
    MESSAGE(STATUS "current platform: Windows")
ELSEIF (CMAKE_SYSTEM_NAME MATCHES "Darwin")
    MESSAGE(STATUS "current platform: Mac OS X")
ELSE ()
    MESSAGE(STATUS "other platform: ${CMAKE_SYSTEM_NAME}")
ENDIF (CMAKE_SYSTEM_NAME MATCHES "Linux")



#cmake_host_system_information(RESULT PRETTY_NAME QUERY DISTRIB_PRETTY_NAME)
#message(STATUS "${PRETTY_NAME}")

#cmake_host_system_information(RESULT DISTRO QUERY DISTRIB_INFO)
#foreach(VAR IN LISTS DISTRO)
    #message(STATUS "${VAR}=`${${VAR}}`")
#endforeach()






set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)
if(MSVC)
#    set(CMAKE_DEBUG_POSTFIX "d")
#    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}  /source-charset:utf-8 /execution-charset:utf-8")
#    set(  CMAKE_CXX_FLAGS   "${CMAKE_CXX_FLAGS}   /fexec-charset=utf-8  /source-charset=utf-8 /execution-charset=utf-8"  )
    #  set(  CMAKE_CXX_FLAGS   "${CMAKE_CXX_FLAGS}  /utf-8 /fexec-charset=utf-8"    )
    #    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -fexec-charset=GBK")
    #     set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -fexec-charset=GBK")
else()
#    set(  CMAKE_CXX_FLAGS   "${CMAKE_CXX_FLAGS}    -fexec-charset=utf-8"    )
endif()
#link_directories(${CMAKE_BINARY_DIR} )

message( "CMAKE_C_COMPILER = ${CMAKE_C_COMPILER}"  )
message( "CMAKE_C_COMPILER_VERSION = ${CMAKE_C_COMPILER_VERSION}"  )
message( "CMAKE_CXX_PLATFORM_ID = ${CMAKE_CXX_PLATFORM_ID}"  )
message( "CMAKE_CXX_COMPILER_TARGET = ${CMAKE_CXX_COMPILER_TARGET}"  )
message( "CMAKE_CXX_COMPILER_AR = ${CMAKE_CXX_COMPILER_AR}"  )
message( "CMAKE_C_COMPILER_ABI = ${CMAKE_C_COMPILER_ABI}"  )
message( "CMAKE_C_COMPILER_TARGET = ${CMAKE_C_COMPILER_TARGET}"  )
message( "CMAKE_HOST_SYSTEM = ${CMAKE_HOST_SYSTEM}"  )
message( "CMAKE_HOST_SYSTEM_NAME = ${CMAKE_HOST_SYSTEM_NAME}"  )
message( "CMAKE_VS_PLATFORM_NAME = ${CMAKE_VS_PLATFORM_NAME}"  )
message( "CMAKE_VS_PLATFORM_TOOLSET = ${CMAKE_VS_PLATFORM_TOOLSET}"  )
message( "CMAKE_CXX_COMPILER_VERSION = ${CMAKE_CXX_COMPILER_VERSION}"  )
#message(  "CMAKE_CXX_COMPILER_TARGET= ${CMAKE_CXX_COMPILER_TARGET}"   )
#message(  "CMAKE_CXX_COMPILER_TARGET= ${CMAKE_CXX_COMPILER_TARGET}"   )
message(  "CMAKE_CXX_COMPILER_ABI= ${CMAKE_CXX_COMPILER_ABI}"   )
message(  "CMAKE_CXX_COMPILER_EXTERNAL_TOOLCHAIN= ${CMAKE_CXX_COMPILER_EXTERNAL_TOOLCHAIN}"   )
message(  "CMAKE_CXX_COMPILER_ID= ${CMAKE_CXX_COMPILER_ID}"   )
message(  "CMAKE_CXX_COMPILER_ARCHITECTURE_ID= ${CMAKE_CXX_COMPILER_ARCHITECTURE_ID}"   )
#message(  "CMAKE_HOST_SYSTEM_NAME= ${CMAKE_HOST_SYSTEM_NAME}"   )
message(  "CMAKE_CXX_STANDARD= ${CMAKE_CXX_STANDARD}"   )
message(  "CMAKE_C_STANDARD= ${CMAKE_C_STANDARD}"   )
message(  "CMAKE_Fortran_COMPILER_ID= ${CMAKE_Fortran_COMPILER_ID}"   )
message(  "CMAKE_CXX_STANDARD= ${CMAKE_CXX_STANDARD}"   )
message(  "CMAKE_C_STANDARD= ${CMAKE_C_STANDARD}"   )
message(  "CMAKE_OSX_ARCHITECTURES= ${CMAKE_OSX_ARCHITECTURES}"   )
message(  "CMAKE_SYSTEM_PROCESSOR= ${CMAKE_SYSTEM_PROCESSOR}"   )
message(  "CMAKE_HOST_SYSTEM_PROCESSOR= ${CMAKE_HOST_SYSTEM_PROCESSOR}"   )
message(  "CMAKE_CUDA_ARCHITECTURES= ${CMAKE_CUDA_ARCHITECTURES}"   )


# 鏀瑰彉瀹夎璺緞鍙互浣跨敤涓嬮潰鐨勮鍙ワ紝Unix: "/usr/local", Windows: "c:/Program Files/${PROJECT_NAME}" 涓洪粯璁ゅ€硷紝鎵€鏈夌殑DESTINATION鍧囦互姝ょ洰褰曚负鏍圭洰褰?
# set(CMAKE_INSTALL_PREFIX ${CMAKE_BINARY_DIR}/mymath)
#set(CMAKE_INSTALL_PREFIX ${CMAKE_BINARY_DIR}/../${PROJECT_NAME}_${PROJECT_VERSION}_${CMAKE_HOST_SYSTEM}_${CMAKE_CXX_COMPILER_ID}_${CMAKE_CXX_COMPILER_VERSION}_install)
set(CMAKE_INSTALL_PREFIX ${CMAKE_BINARY_DIR}/../${PROJECT_NAME}_${PROJECT_VERSION}_${CMAKE_HOST_SYSTEM_NAME}_${CMAKE_CXX_PLATFORM_ID}_${CMAKE_CXX_COMPILER_ID}_${CMAKE_CXX_COMPILER_VERSION}_${CMAKE_Fortran_COMPILER_ID}_${CMAKE_Fortran_COMPILER_VERSION}_CXX_${CMAKE_CXX_STANDARD}_${CMAKE_SYSTEM_PROCESSOR}_install)


set(OUTPUT_DIR_KENT   ${CMAKE_BINARY_DIR}/../${PROJECT_NAME}_${PROJECT_VERSION}_${CMAKE_HOST_SYSTEM_NAME}_${CMAKE_CXX_PLATFORM_ID}_${CMAKE_CXX_COMPILER_ID}_${CMAKE_CXX_COMPILER_VERSION}_${CMAKE_Fortran_COMPILER_ID}_${CMAKE_Fortran_COMPILER_VERSION}_CXX_${CMAKE_CXX_STANDARD}_${CMAKE_SYSTEM_PROCESSOR}_bin )
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY   ${OUTPUT_DIR_KENT} )
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY    ${OUTPUT_DIR_KENT} )
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY    ${OUTPUT_DIR_KENT} )





# install
include(CMakePackageConfigHelpers)

add_subdirectory( MyMath )

add_subdirectory( minus )

add_subdirectory( app )
