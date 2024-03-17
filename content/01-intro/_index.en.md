+++
archetype = "chapter"
title = "Ikea device"
weight = 1

+++

## The device

This projects accesses the Ikea **VINDSTYRKA air quality sensor** raw data and send them to [Thingspeak](https://thingspeak.com/) channels, which can therefore visualized in a the comprehensive homepage.

![](ikea.jpeg)

To do so, you will need:

- a microcontroller (such as ESP32, ESP8266 or a D1 Mini)
- some jumpers to solder your micro to the sensor
- basic soldering skills
- screwdrives: the outer screws are heaxagon, while the inner ones are classical phillips
- a (free) thingspeak account

The Ikea VINDSTYRKA is based on the SEN54 sensor, which is the top choice for its price class. Providing good accuracy for 10+ years. It measure PM1.0, PM2.5, PM4.0, PM10.0 (these last two with less accuracy then the other two.), temperature humidity and tvoc.

[Sensirion SEN54](https://sensirion.com/products/catalog/SEN54/)