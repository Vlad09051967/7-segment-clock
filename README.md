# 7-segment-clock

# Introduction
This project was created for a 3D printable 7 segment clock. You can find more information on Thingiverse https://www.thingiverse.com/thing:2947883.

# Installation
1. Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software)
1. Install the [CH340G driver](https://wiki.wemos.cc/tutorials:get_started:get_started_in_arduino)
1. In the preferences dialog of the Arduino IDE, add http://arduino.esp8266.com/stable/package_esp8266com_index.json to the Additional Boards Manager URLs
1. Open Boards Manager (under Tools), search for and install the latest version of esp8266.
1. Install libraries using the Library Manager (Sketch > Include Library > Manage Libraries):
    - [WiFiManager](https://github.com/tzapu/WiFiManager)
    - [ArduinoJSON](https://arduinojson.org) (version 5.x, not 6.x!)
    - [FastLED](https://github.com/FastLED/FastLED)
1. Install [PaulStoffregen's Time library](https://github.com/PaulStoffregen/Time):
    - Download the library as a zip (master branch) https://github.com/PaulStoffregen/Time/archive/master.zip
    - Sketch > Include Library > Add .ZIP library...
    - Open the Time-master directory in your sketchbook location (find it under Preferences > Sketchbook location)
    - rename Time.h to \_Time.h (this is to avoid a [conflict with time.h](https://github.com/mikalhart/IridiumSBD/issues/16) on some OSs)
1. Install the [Arduino ESP8266 filesystem uploader plugin](https://github.com/esp8266/arduino-esp8266fs-plugin) (requires restart of IDE)
1. Connect your D1 mini to the computer using a micro USB cable
1. Under Tools, select "LOLIN(WEMOS) D1 R2 & mini" as the board
1. Tools > Flash Size > 4M (FS:1MB OTA:~1019KB)
1. Tools > Port > (pick the one that corresponds to your USB com port)
1. Open [clock.ino](Arduino/clock.ino)
1. Sketch > Upload
1. Upload the sketch data files (the [data](Arduino/data) directory in the sketch folder) using Tools > ESP8266 Sketch Data Upload.
1. If you want to use the Serial Monitor (Tools > Serial Monitor) for troubleshooting, be sure to change the baud rate to 115200 to match the baud rate specified in the sketch code

# Initial Configuration
1. When the sketch runs for the first time, the D1 mini will try to connect to your wifi and fail (because it doesn't have any previously saved wifi credentials). This will cause it to start up an access point, which serves up a captive configuration portal (thanks to [WiFiManager](https://github.com/tzapu/WiFiManager).
1. You can connect to this access point to select and enter credentials for your network
1. You will also enter your [ipstack.com](https://ipstack.com/) API key and [Google Time Zone](https://developers.google.com/maps/documentation/timezone/get-api-key)/[Google Maps Javascript](https://developers.google.com/maps/documentation/javascript/get-api-key) API key on this screen
1. Save (the D1 mini will restart and connect to your wifi)

# Runtime Configuration
1. While connected to the same network as the D1 mini, open a browser and go to http://\<IP of D1 mini> (you can find the D1 mini's IP address using your router).
![web UI](web.png)
