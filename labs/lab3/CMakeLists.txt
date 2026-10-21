file(GLOB_RECURSE LAB3_SOURCES CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")
list(REMOVE_ITEM LAB3_SOURCES
    "${CMAKE_CURRENT_SOURCE_DIR}/main.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/demo.cpp"
)

# игра
add_executable(lab3 main.cpp ${LAB3_SOURCES})
target_include_directories(lab3 PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}")

# демонстрация паттернов - отдельная программа со своей функцией main, собирается, если есть demo.cpp
if(EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/demo.cpp")
    add_executable(lab3_demo demo.cpp ${LAB3_SOURCES})
    target_include_directories(lab3_demo PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}")
endif()
