add_subdirectory(esp8266-cmake/main)
add_subdirectory(esp8266-cmake/arduino)

### WiFi library
file(GLOB WIFI_LIB_SRC
    ${CMAKE_CURRENT_LIST_DIR}/Arduino/libraries/ESP8266WiFi/src/*.cpp
)

add_library(wifi STATIC
    ${WIFI_LIB_SRC}
)

target_include_directories(wifi PUBLIC
    ${CMAKE_CURRENT_LIST_DIR}/Arduino/libraries/ESP8266WiFi/src
)

target_link_libraries(wifi PUBLIC
    arduino
)

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
    wifi
)

