cmake_minimum_required(VERSION 3.28)
project(PNZ LANGUAGES CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

include(FetchContent)
FetchContent_Declare(SFML
    GIT_REPOSITORY https://github.com/SFML/SFML.git
    GIT_TAG 3.0.0
    GIT_SHALLOW ON
    EXCLUDE_FROM_ALL
    SYSTEM)
FetchContent_Declare(json
    GIT_REPOSITORY https://github.com/nlohmann/json
    GIT_TAG v3.11.3
)
FetchContent_MakeAvailable(SFML json)

add_executable(main src/main.cpp src/Menu.cpp)

target_link_libraries(main PRIVATE
    SFML::Window
    SFML::System
    SFML::Audio
    SFML::Graphics
    nlohmann_json::nlohmann_json
)
