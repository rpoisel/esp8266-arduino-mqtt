add_subdirectory(esp8266-cmake/main)
add_subdirectory(esp8266-cmake/arduino)

### WiFi library
add_library(WIFI_LIB INTERFACE)
set_property(TARGET WIFI_LIB
    PROPERTY INTERFACE_INCLUDE_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/Arduino/libraries/ESP8266WiFi/src
    )

file(GLOB WIFI_LIB_SRC
    ${CMAKE_CURRENT_LIST_DIR}/Arduino/libraries/ESP8266WiFi/src/*.cpp
)

add_library(wifi STATIC
    ${WIFI_LIB_SRC}
)

target_include_directories(wifi PRIVATE
    $<TARGET_PROPERTY:WIFI_LIB,INTERFACE_INCLUDE_DIRECTORIES>
    $<TARGET_PROPERTY:arduino,INCLUDE_DIRECTORIES>
)

target_compile_definitions(wifi PUBLIC
    $<TARGET_PROPERTY:arduino,COMPILE_DEFINITIONS>
)

target_compile_options(wifi PUBLIC
    $<TARGET_PROPERTY:arduino,COMPILE_OPTIONS>
)

### MQTT library
add_library(PUBSUBCLIENT_LIB INTERFACE)
set_property(TARGET PUBSUBCLIENT_LIB
    PROPERTY INTERFACE_INCLUDE_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/pubsubclient/src
    )

file(GLOB PUBSUBCLIENT_LIB_SRC
    ${CMAKE_CURRENT_LIST_DIR}/pubsubclient/src/*.c
    ${CMAKE_CURRENT_LIST_DIR}/pubsubclient/src/*.cpp
)

add_library(pubsubclient STATIC
    ${PUBSUBCLIENT_LIB_SRC}
)

target_include_directories(pubsubclient PRIVATE
    $<TARGET_PROPERTY:WIFI_LIB,INTERFACE_INCLUDE_DIRECTORIES>
    $<TARGET_PROPERTY:PUBSUBCLIENT_LIB,INTERFACE_INCLUDE_DIRECTORIES>
    $<TARGET_PROPERTY:arduino,INCLUDE_DIRECTORIES>
)

target_compile_definitions(pubsubclient PUBLIC
    $<TARGET_PROPERTY:arduino,COMPILE_DEFINITIONS>
)

target_compile_options(pubsubclient PUBLIC
    $<TARGET_PROPERTY:arduino,COMPILE_OPTIONS>
)
