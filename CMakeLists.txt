cmake_minimum_required(VERSION 3.19)
project(uriparser)
add_library(${PROJECT_NAME} STATIC)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

file(GLOB_RECURSE URIPARSER_SOURCES CONFIGURE_DEPENDS src/*.c src/*.h)
target_sources(${PROJECT_NAME} PRIVATE ${URIPARSER_SOURCES})
message("target: ${PROJECT_NAME} source files: ${URIPARSER_SOURCES}")

set_target_properties(${PROJECT_NAME} PROPERTIES
  C_STANDARD 17
  C_STANDARD_REQUIRED ON
  C_EXTENSIONS OFF
)
target_compile_definitions(${PROJECT_NAME} PUBLIC -DURI_STATIC_BUILD)
