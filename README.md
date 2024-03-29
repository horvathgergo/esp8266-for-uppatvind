# Smart Air Purifier (Project Uppåtvind)
Custom PCB based on ESP12-F (ESP8266) wifi module that serves as a smart controller for IKEA Uppåtvind Air Purifiers. It's embedded microcontroller enables you to incorporate your device to home automation systems (preferably to Home Assistant) or control it via custom mobile applications as it enjoys support from wide variety of firmwares. This project was implemented in two major phases. Hardware was designed with KiCAD, software is based on MicroPython.

About IKEA Uppåtvind: It is the newest air purifier of the swedish company, compact and even smaller than its older borther, Förnuftig. It effectively cleans the indoor air from harmful PM2.5 particles and pollen for cheap (price approx. EUR30). The device is optimised for small bedrooms and has three fan speed. 

Current status of the development: **Finalized**

Hardware: 
* [x] Schematic
* [x] Layout
* [x] BOM, CPL
* [x] 3D model 
* [x] Testing

Software:
* [X] MicroPython


## Hardware

<img src="https://user-images.githubusercontent.com/44551566/227743230-bfe3b7a5-8919-44fc-974f-6e5c604d3f0f.png" width="700" height="400">

PCB has the same size as the original one (70x36 mm) with mounting holes placed on it, thus it is supposed to fit just fine inside the plastic housing. Power supply of the fan is +24V, 0.8A. The board has a MC34063DR switching voltage regulator that provides the necessary power (+3v3, >500mA) for the wifi module. With the onboard physical button you can toggle the fan (turn on/off or even change speed). Two blue LEDs are connected to the ESP pins so it can indicate changes in operating mode. Note: to avoid unnecessary costs and save some space on the board physical filter reset button is not incorporated in this version as this function can be easily achieved through software side. 

The Purifier has a 4-pin PWM fan with +24VDC, 0.5A. The pins are POWER, GND, PWM, FG. PWM is a control pin for pulse width modulation and FG is the tacho pin for feedback purposes. The fan operates with a constant duty cycle of 50% and variable frequency between ca. 1-300Hz.

![475CF212-3C40-45C2-A7EA-1FA76863B281](https://user-images.githubusercontent.com/44551566/228315095-3f7911fd-b2ab-4ef3-aa52-a557d3de73f2.jpeg)

MCU programming: the board supports only UART programming via TX, RX pin headers (no USB interface), thus USB to TTL converter is necessary to upload firmware. It is recommended to supply the module via VIN and GND pins when programming. It is compatible with +5-24V supply (but +3V3 supply is not guaranteed to work as you may experience some voltage drop via the buck converter so make sure to provide enough voltage during flashing). Boot button is located on the right side of the wifi module.

BOM: Most of the chosen components are considered to be basic/standard parts at LCSC, however there are some extended components on the list (two large cap, inductor, esp, jst connectors and uart pin headers, tactile switch).

## Software

The software for Uppåtvind has been developed in Micropython. It enables the device to be controlled via mqtt while exploits Home Assistant mqtt autodiscovery features that provides with a smooth (almost zero config) setup process. 

More detailed description is available in this repo: https://github.com/horvathgergo/uPurifier

## Contribution

If you find this project useful please support its further development by using the button below:

<a href="https://www.buymeacoffee.com/gergohorvath"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=gergohorvath&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>
