cmake_minimum_required(VERSION 3.5)
project(UAVProduct)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD 11)

#gdal include and linrary files
set(GDAL_LIBRARY "/usr/local/lib/libgdal.so")
set(GDAL_INCLUDE "/usr/local/include/")
set(SIFT_LIBRARY "/usr/local/lib/libvlsift.a")
set(EXIF_LIBRARY "/usr/local/lib/libeasyexif.a")
set(GTest_LIBRARY "/usr/local/lib/libgtest.a")

#openMVG
find_package(OpenMVG REQUIRED)
find_package(OpenMVS REQUIRED)
find_package(GTest REQUIRED)

include_directories(${GTEST_INCLUDE_DIRS})
include_directories(${OPENMVG_INCLUDE_DIRS})
include_directories(${GDAL_INCLUDE})
include_directories(${OpenMVS_INCLUDE_DIRS})

set(SOURCE_FILES UAVMain.cpp)

add_executable(UAVProcess ${SOURCE_FILES})

target_link_libraries(UAVProcess ${OPENMVG_LIBRARIES})
target_link_libraries(UAVProcess ${OpenMVS_LIBRARIES})
target_link_libraries(UAVProcess ${GTEST_LIBRARIES})

target_link_libraries(UAVProcess ${GDAL_LIBRARY})
target_link_libraries(UAVProcess ${SIFT_LIBRARY})
target_link_libraries(UAVProcess ${EXIF_LIBRARY})