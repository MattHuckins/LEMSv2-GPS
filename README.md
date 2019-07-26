# LEMSv2-GPS
LEMSv2 GPS w/standalone option

## Intro

The LEMSv2 is an open source environmental monitoring station, which was designed to be deployed for extended periods of time and powered by a 5W solar panel (More information can be found on Madvoid's LEMSv2 GitHub page.

## Objective
The objective of this project is to incorperate a GPS module into the existing LEMSv2 system, while considering the low energy consumption goals of the original LEMSv2 environmental monitoring system. The two main goals of the this project are: to use the GPS module to update the RTC if the system malfunctions in a manner that resets the RTC, to datalog multiple location data to an SD card for the purpose of secondary statistical analysis.

## Library additions to the original LEMSv2

#include "variant.h"            // Multiplexing library for SAMD boards

<TinyGPS++.h>          // TimyGPS++ a GPS library

#include <RTClibExtended.h>             // RTC Library - https://github.com/adafruit/RTClib

// added '#define _BV(bit) (1 << (bit))' to RTClibExtended.h

The one line of code must be added to the RTClibExtended.h file to fix a known issue with a bit being off.

## Known issues

-If you attempt to set the time in a completely indoor location, void of windows, the time will be set to 01/01/2000.

-It was randomly observed that the SD card failed initialize and properly store the data in 1 of the 30 trail runs prior to the write up. Research on forums indicates that the default SD library has been observed to behave unusually.
--
## Items to be selected

Controllable voltage regulator to be controlled by digital pin 4 for the powering on and off of the GPS module

## Future recommnendations

  - remove or increase the timeout duration in the defined GPS location function in the code, in the event that system is deployed in heavily forested area, or in location with robust obstructions

  - NEO GPS: a more efficient and powerful GPS library, instead of tinyGPS++

  - To account for differing satelite locations and satelite 'drift' that will possibly be observed in the recorded location data at different times throughout the day, record GPS location multiple times throughout the day

  - For additional power saving purposes to the general (and original) LEMSv2 datalogging feature, it may be beneficial to utilize the RAM on the SAMD 21 board. This could be done by logging weather data blocks in RAM, allowed by the total availible RAM, and then sending the blocks of data to the SD card instead of logging one row of data at a time to the SD card.
