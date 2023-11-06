# esp12-thermometer

*Work in progress*

This project aims to build a small thermometer using an ESP8266
and [ESPHome](https://esphome.io/) to deliver those values to 
homeassistant. The goal is to make the build as small and power efficient
as possible with WiFi.
For this the follwing components are used:
1. ESP8266-01
2. An AHT-20 breakout board which  had lying around.
    It measures temperature and humidity
3. An optional battery with protection circuit