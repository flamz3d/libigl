get_filename_component(PROJECT_NAME ${CMAKE_CURRENT_SOURCE_DIR} NAME)
project(${PROJECT_NAME})

add_library(${PROJECT_NAME} MODULE main.cpp)
set_target_properties(${PROJECT_NAME} PROPERTIES BUNDLE TRUE)
target_link_libraries(${PROJECT_NAME} igl::core)
