How to use CLION with ARDUINO
=============================



CMakeLists.txt
==============

Apply those changes to setup COM port and Arduino board type.
````
#### Uncomment below additional settings as needed.
set(${CMAKE_PROJECT_NAME}_BOARD mega)
set(${CMAKE_PROJECT_NAME}_PORT COM6)
set(mega.build.mcu atmega2560)
set(mega.upload.protocol wiring)
set(mega.upload.speed 115200)

LINK_DIRECTORIES(C:\\Program Files (x86)\\Arduino\\libraries)
````



Usefull links:
==============

https://www.instructables.com/id/Setup-JetBrains-Clion-for-Arduino-Development/
https://arduino.stackexchange.com/questions/20294/clion-arduino/26482

Serial port monitoring:
https://plugins.jetbrains.com/plugin/8031-serial-port-monitor


Still not found:
================
How to remove git path as CMAKE is complaining because:
- it's not set in SYSTEM ENV