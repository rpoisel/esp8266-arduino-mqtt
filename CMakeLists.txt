project("ESP8266 Arduino" C CXX ASM)
cmake_minimum_required(VERSION 3.0)

add_subdirectory(external)

add_subdirectory(user)

target_link_libraries(USER_CODE INTERFACE
    user_lib
    wifi
    pubsubclient
    arduino
)
