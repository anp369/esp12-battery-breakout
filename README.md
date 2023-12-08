# esp12-thermometer

*Work in progress*

This project aims to build a small thermometer using an ESP8266
and [ESPHome](https://esphome.io/) to deliver those values to 
homeassistant. The goal is to make the build as small and power efficient
as possible with WiFi.

It features an breakout and 4,7 k pull up resistors for I²C and One Wire.
Programing is accomplished via test pads on one edge, which can 
be clamped on to with crocodile clips.
Then use your favorite serial adapter to connect to the board. 

### Rendered board
<p float="left">
  <img src="res/render_front.png" width="49%">
  <img src="res/render_back.png" width="49%">
</p>

The whole board only measures 36 mm  * 28 mm.
Height depends on whether you use a battery and on the sensors you are using.

### Features
* Input voltage: 3.0 < V_in < 5.5
* ESP12 as microcontroller
* TP4056 based charging and protection circuit for Li batteries
* integrated 3,3 V LDO voltage regultor
* pullup resistors for I²C and OneWire
* Programming via test pads

### Assembly
There are some things to consider depending if you use a battery or
a power supply to power this project.
The voltage regulator only can deliver about 500 mA.
Make sure to not draw to much current with any additional sensors.

##### Battery
1. Check that your battery supports the selected charging current of the
   charging circuit. This can be set by a resistor. See the [datasheet](https://dlnmh9ip6v2uc.cloudfront.net/datasheets/Prototyping/TP4056.pdf) for more 
   information on which resistor value to set.
2. Make sure to populate Q1 as it prevents from charging and powering the 
   circuit at the same time. This is not supported by the charger and should be
   avoided.
3. Solder your battery directly to the `BATT` terminal or solder in the
   fitting connector

##### Power supply
1. Short JP3 and don't populate Q1 and U1.  
   This makes connection between the
   `5V` pad and the supply rail.
2. Connect your power supply to `5v` and `GND`.

### Programming
1. Connect to the test pads with some test probes or crocodile clips.
   Make sure to match `RX` and `TX` to be crossed with your programmer :) 
2. Short `PRGM` and `RST` jumpers with a metal object to set the ESP into
   bootloader mode. Now you can start the programming process. 
   (`esptool` or directly from `esphome`)
