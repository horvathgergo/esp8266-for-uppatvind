# Smart Air Purifier (Project Uppatvind)
Custom PCB based on ESP12-F (ESP8266) wifi module that serves as a smart controller for IKEA Uppatvind Air Purifiers. It's embedded microcontroller enables you to incorporate your device to home automation systems (preferably to Home Assistant) or control it via custom mobile applications as it enjoys support from wide variety of firmwares. This project is going to be implemented in two simple major phases: Hardware and Software design. Hardware is designed with KiCAD, manufactured with assembly services by a reputable Chinese company. Software is planned to be based on MicroPython and ESPHome firmwares.

Current status of the development: **Prototype is ready to order**

Hardware: 
* [x] Schematic finished
* [x] Components, layout finished
* [x] 3D model finished
* [ ] Testing (hasn't started yet)

Software:
* [ ] ESPHome
* [ ] MicroPython


## Hardware

PCB is the same size of the original one (70x36 mm) with mounting holes placed on it, thus it is supposed to fit just fine inside the plastic housing. Power supply of the fan is +24V, 0.8A. The board has a MC34063DR switching voltage regulator that provides the necessary power (+3v3, >500mA) for the wifi module. With the onboard physical button you can toggle the fan (turn on/off or event to change speed). Two LED (blue and red) are connected to the ESP pins so it can indicate changes in operating mode. Note: to avoid unnecessary costs and save some space on the board physical filter reset button is not incorporated in this version as this function can be easily achieved through software side. 

MCU programming: the board supports only UART programming via TX, RX pin headers (no USB interface), thus USB to TTL converter is necessary to upload firmware. It is recommended to supply the module via VIN, GND pins also when programming. It is compatible with +24V and +5V supply (but +3V3 supply is not guaranteed to work as you may experience some voltage drop via the buck converter so make sure to provide enough voltage during flashing). Boot button is located on the right side of the wifi module.


## Contribution

If you find this project useful please support further development by using the button below:

<a href="https://www.buymeacoffee.com/gergohorvath"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=gergohorvath&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>
