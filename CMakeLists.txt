project(stream-unrar)
cmake_minimum_required(VERSION 2.8)

add_subdirectory(3rd_party)
include_directories(3rd_party/unrar-4.0.7)

list(APPEND EXE_SRC stream_unrar.cpp backend/FilePoller.cpp)

if (UNIX)
	list(APPEND EXE_SRC backend/FilePollerPOSIX.cpp)
	list(APPEND EXE_SRC backend/FilePollerGeneric.cpp)
endif()

add_executable(stream-unrar ${EXE_SRC})
target_link_libraries(stream-unrar unrar)
