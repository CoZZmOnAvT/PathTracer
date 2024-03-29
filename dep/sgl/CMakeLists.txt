cmake_minimum_required(VERSION 3.5.2)
project(sgl LANGUAGES C VERSION 0.0.1)

list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake")

find_package(SDL2 REQUIRED)
find_package(SDL2_ttf REQUIRED)
find_package(SDL2_image REQUIRED)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wextra -Wall -Werror")
set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -g -O0")
set(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} -O3")

set(PROJECT_SRC_DIR "${PROJECT_SOURCE_DIR}/src")
set(PROJECT_HEADERS_DIR "${PROJECT_SOURCE_DIR}/include")

file(GLOB SOURCES ${PROJECT_SRC_DIR}/*.c)

add_library(${PROJECT_NAME} STATIC ${SOURCES})
target_link_libraries(${PROJECT_NAME}
  PRIVATE ft
  PUBLIC SDL2 SDL2_ttf SDL2_image
)
target_include_directories(${PROJECT_NAME} PUBLIC ${PROJECT_HEADERS_DIR})
