#This CMakeLists do not use mpi-intel but sgi-mpt since
#boost.mpi is compiled with sgi-mpt

cmake_minimum_required(VERSION 2.8)
set(CMAKE_C_COMPILER icc)
set(CMAKE_CXX_COMPILER icpc)
set(MPI_COMPILER icpc)
project(boost_mpi)
find_package(Boost COMPONENTS mpi serialization)
include_directories(${Boost_INCLUDE_DIRS})
link_directories(${Boost_LIBRARY_DIRS})
set(exe_name prog)
add_executable(${exe_name} main.cpp)
target_link_libraries(${exe_name} ${Boost_LIBRARIES})
target_link_libraries(${exe_name} mpi)
