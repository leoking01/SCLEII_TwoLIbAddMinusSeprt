project(TestInstallation)
cmake_minimum_required(VERSION 3.5)

set(MyMath_root_dir "E:\\AAAAA_cmk_lib_export\\SCLEII_TwoLIbAddMinusSeprt_19.33.31630.0_install")

find_package(MyMath 1.0 PATHS ${MyMath_root_dir} )

find_package(minus 1.0 PATHS ${MyMath_root_dir} )


add_executable(mymathApp mymathApp.cc)

target_link_libraries(mymathApp MyMath::mymath minus::minus )
#
target_include_directories( mymathApp PRIVATE ${MyMath_root_dir}/include  )
