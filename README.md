# RS41HUP (Ham Use Project) Beacon version
Alternative firmware version based on DF8OE's firmware for ham radio use.
I felt the necessity to modify the original firmware in order to make a versatile, reliable and light firmware to allow the usage of the RS41 radiosondes made by Vaisala as ham radio beacons using A1A modulation (CW).
APRS-related code has been removed, RTTY is still present (for now).

Please note that a lot of refactoring is still needed, and that config.h file still contains settings that won't have any effect on the actual way the radiosonde beacon works (eg: RTTY_TO_MORSE_RATIO won't have any effect at all, since it won't transmit via RTTY).

Released under GPL v2


# Windows:

Use:
https://www.wyzbee.com/download/Utilities/Software/CoIDE-1.7.8.exe

And:
https://launchpad.net/gcc-arm-embedded/5.0/5-2016-q3-update/+download/gcc-arm-none-eabi-5_4-2016q3-20160926-win32.exe


# Linux:
Maybe you have to set correct path to gcc-arm-none-eabi in CMakeLists.txt.<br><br>

cd into main folder

cmake .

make

# Configuration
All configs in ```config.h```

* ```SEND_RTTY_<value>``` Include <value> into the RTTY packet
* ```RTTY_CALLSIGN``` RTTY callsign
* ```RTTY_COMMENT``` RTTY comment
* ```RTTY_WWL``` Send WWL instead of the RTTY comment
* ```PAIR_COUNT``` World Wide Locator pairs (precision)
* ```RTTY_FREQUENCY``` RTTY frequency in MHz
* ```RTTY_DEVIATION``` RTTY shift configurable in 270Hz steps
* ```RTTY_SPEED``` RTTY speed in bauds
* ```RTTY_7BIT``` Use 7 bit RTTY
* ```RTTY_USE_2_STOP_BITS``` Use 2 stop bits

* ```SEND_MORSE_<value>``` Include <value> into the Morse message
* ```MORSE_SUFFIX``` Optional end of the Morse message (ar^)
* ```MORSE_WPM``` Morse speed in words per minute
* ```RTTY_TO_MORSE_RATIO``` Number of RTTY frames between each Morse message
* ```TX_POWER``` Power 0-7, (7 means 42.95 mW@434.150 MHz measured on E4406A)
* ```ALLOW_DISABLE_BY_BUTTON``` Allow disabling device using button
* ```TX_DELAY``` Delay between RTTY frames in milliseconds
* ```LED_ENABLED``` Optionally /disable LED blinking (takes effect after approx. 10 minutes)


Have a nice day ;)

# Changelog
 * 14.12.2016 - Reverse engineeded connections, initial hard work, resulting in working RTTY by SQ7FJB
 * 07.01.2017 - GPS now using proprietiary UBLOX protocol, more elastic code to set working frequency by SQ5RWU
 * 23.01.2017 - Test APRS code, small fixes in GPS code by SQ5RWU
 * 06.06.2017 - APRS code fix, some code cleanup
 * June 2017 - starting with Linux support, making configuration more flexible by DF8OE
 * November 2018 by OK1TE
     * Optionally alter the RTTY comment with the World Wide Locator
     * Made the RTTY packet content configurable
     * Optionally turn off RTTY or APRS
     * Optionally turn off LED blinking
     * Added Morse (CW) support
 * 22.09.2019 - Removed (almost) all APRS-related code
 * 26.09.2019 - Added function to return GPS seconds, used in main() to start CW transmission at given seconds


# TODO
 * Adding support for EmbiTZ IDE
 * Adding support for platform independent IDE Eclipse
 * More APRS config options
 * Temperature and moisture sensor
 * Pressure sensor
 * implementing protocol for using external devices on extension header
 * Configuration via extension header (serial connection) without need for reflashing firmware
 * Possibly add configuration "wireless" using RFID loop present in sonde
