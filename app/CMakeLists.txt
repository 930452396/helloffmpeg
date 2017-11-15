# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

add_library( avutil-54
             SHARED
             IMPORTED )
set_target_properties( avutil-54
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../libs/armeabi/libavutil-54.so )

add_library( swresample-1
             SHARED
             IMPORTED )
set_target_properties( swresample-1
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../libs/armeabi/libswresample-1.so )
add_library( avcodec-56
             SHARED
             IMPORTED )
set_target_properties( avcodec-56
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../libs/armeabi/libavcodec-56.so )
add_library( avfilter-5
             SHARED
             IMPORTED)
set_target_properties( avfilter-5
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../libs/armeabi/libavfilter-5.so )
add_library( swscale-3
             SHARED
             IMPORTED)
set_target_properties( swscale-3
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../libs/armeabi/libswscale-3.so )
add_library( avdevice-56
             SHARED
             IMPORTED)
set_target_properties( avdevice-56
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../libs/armeabi/libavdevice-56.so )
add_library( avformat-56
             SHARED
             IMPORTED)
set_target_properties( avformat-56
                       PROPERTIES IMPORTED_LOCATION
                       ../../../../libs/armeabi/libavformat-56.so )

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11")

add_library( native-lib
             SHARED
             src/main/cpp/native-lib.cpp )

include_directories(libs/include)

#target_include_directories(native-lib PRIVATE libs/include)

target_link_libraries( native-lib avutil-54 swresample-1 avcodec-56 avfilter-5 swscale-3 avdevice-56 avformat-56
                       ${log-lib} )
