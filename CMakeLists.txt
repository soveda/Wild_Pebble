cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(wild_pebble)

pico_sdk_init()

add_executable(wild_pebble
    main.cpp
)

target_include_directories(wild_pebble PRIVATE
    ../../Demonstrations+HelloWorlds/PicoSDK/ComputerCard
)

target_compile_definitions(wild_pebble PRIVATE
    PICO_XOSC_STARTUP_DELAY_MULTIPLIER=64
)

target_compile_options(wild_pebble PRIVATE
    -Wall
    -Wextra
    -Wdouble-promotion
    -Wfloat-conversion
)

target_link_libraries(wild_pebble
    pico_stdlib
    pico_unique_id
    hardware_adc
    hardware_spi
    hardware_pwm
)

# Strongly recommended for stable timing.
pico_set_binary_type(wild_pebble copy_to_ram)

pico_enable_stdio_usb(wild_pebble 0)

pico_add_extra_outputs(wild_pebble)
