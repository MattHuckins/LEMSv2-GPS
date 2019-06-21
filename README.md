# LEMSv2-GPS
LEMSv2 GPS w/standalone

## Intro

The LEMSv2 is an open source environmental monitoring station, which was design designed to be deployed for extended periods of time and powered by a 5W solar panel (More information can be found on Madvoid's LEMSv2 GitHub page.

## Objective

## Library additions

## Summary of functionallity

## Known issues

## Items to be selected

Controllable voltage regulator to be controlled by digital pin 4.

## Future recommnendations

NEO GPS: a more efficient and powerful GPS library

For additional power saving purposes to the general (and original) LEMSv2 datalogging feature, it may be beneficial to utilize the RAM on the SAMD 21 board. This could be done by logging weather data blocks in RAM, allowed by the total availible RAM, and then sending the blocks of data to the SD card instead of logging one row of data at a time to the SD card.
