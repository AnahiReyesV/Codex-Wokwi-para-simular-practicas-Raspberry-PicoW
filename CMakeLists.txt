cmake_minimum_required(VERSION 3.13)

project(pico_keypad_led_controller C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# This project source follows an Arduino-style setup()/loop() pattern.
# Keep as reference for repository organization and documentation.
add_executable(pico_keypad_led_controller
    src/main.cpp
)
