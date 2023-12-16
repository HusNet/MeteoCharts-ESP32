cmake_minimum_required(VERSION 3.27)
set(CMAKE_TOOLCHAIN_FILE ${CMAKE_SOURCE_DIR}/cmake/ArduinoToolchain.cmake)
set(PROJECT_NAME MeteoCharts_ESP32)

project(${PROJECT_NAME})

set(${PROJECT_NAME}_SKETCH MeteoCharts.ino) # Default Sketch

generate_arduino_firmware(${CMAKE_PROJECT_NAME}
         SRCS MeteoCharts.ino
         LIBS Wire SPI Adafruit_GFX Adafruit_ILI9341 Adafruit_BME280 Adafruit_Sensor Adafruit_BusIO
         BOARD esp32c3_dev_module
         SERIAL picocom @SERIAL_PORT@ -b 115200 -l
         PORT /dev/ttyUSB0)

