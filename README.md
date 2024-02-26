# AlbinoAir

this projects aims to access the Ikea VINDSTYRKA air quality sensor raw data. 
To do so, a microcontroller (such as Arduino or Esp32) is used.

The Ikea VINDSTYRKA is based on the SEN54 sensor, which is the top choice for its price class.
https://sensirion.com/products/catalog/SEN54/

resulting website (aestetichs greatly improvable): https://novecento99.github.io/AlbinoAir/


## Build this project

First, you have to tear down the device. 
User @oleksiikutuzov provided great pictures about it: https://github.com/oleksiikutuzov/IKEA-VINDSTYRKA/blob/main/teardown.md

You need to solder 4 jumpers:
- Vcc (5V or 3V depending on your microcontroller supply voltage)
- GND
- SDA
- SCL

I highly suggest to unpin the display connector and to unscrew the PCB completly before soldering.
If you do not want to risk the PCB, you can also opt to cut the cables running from the PCB to the sensor and connecting the jumpers to them, while also resoldering them.

<img src="Images/PCB.jpeg" width="500px">

You can now connect your microcontroller, DSA and SCL are the two I2C protocol wires.
The DSA and SCL corresponds to pins specific to the board your using. 
For example, the Esp8266 Nodemcu has as default pins D1 and D2.
You can easily find them by googling "xxxxx board I2C default pins".




## Authors

- [@Novecento99](https://github.com/Novecento99/AlbinoAir/)


## Optimizations

- esp sleep instead of delay to save power
- better webpage user experience
- fix the upload time (e.g. at xx:00)
- improve the website

- connection to google home

## Acknowledgements

I want to thankyou @XXXX for the teardown that showed the possiblity to connect a microcontroller,
  @senserison to build a really good sensor 
@ikea to encapsuledet it in a economical good lookkig piece. 
