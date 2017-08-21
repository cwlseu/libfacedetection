cmake_minimum_required(VERSION 2.8)
find_package( OpenCV REQUIRED )

set(source ./example/libfacedetect-example.cpp)
include_directories(./include)

#if you don't want to use openMP, you should comment this line
FIND_PACKAGE( OpenMP REQUIRED)

if(OPENMP_FOUND)
    message("OPENMP FOUND")
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_C_FLAGS}")
    set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_EXE_LINKER_FLAGS}")
endif()


add_executable(libfacedetect ${source})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11") 
target_link_libraries(libfacedetect ${OpenCV_LIBS}) 
