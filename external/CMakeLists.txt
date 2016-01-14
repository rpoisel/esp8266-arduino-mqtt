add_subdirectory(esp8266-cmake/main)
add_subdirectory(esp8266-cmake/arduino)

### MQTT library
file(GLOB PUBSUBCLIENT_LIB_SRC
    ${CMAKE_CURRENT_LIST_DIR}/pubsubclient/src/*.c
    ${CMAKE_CURRENT_LIST_DIR}/pubsubclient/src/*.cpp
)

add_library(pubsubclient STATIC
    ${PUBSUBCLIENT_LIB_SRC}
)

target_include_directories(pubsubclient PUBLIC
    ${CMAKE_CURRENT_LIST_DIR}/pubsubclient/src
)

target_link_libraries(pubsubclient PUBLIC
    arduino
    esp8266wifi
)

