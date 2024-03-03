# AlbinoAir

this projects accesses the Ikea VINDSTYRKA air quality sensor raw data and send them to thingspeak channels, which can therefore visualized in a comprehnsive website (e.g. https://novecento99.github.io/AlbinoAir/) (yeah I'm not good at making websites). 

<img src="Images/ikea.jpeg" width="500px">

To do so, you will need:
- a microcontroller (such as ESP32, ESP8266 or an Arduino with wifi shield)
- some jumpers
- basic soldering skills
- screwdrivers

The Ikea VINDSTYRKA is based on the SEN54 sensor, which is the top choice for its price class. Providing good accuracy for 10+ years.
https://sensirion.com/products/catalog/SEN54/


## How to build this project


### step 1: teardown and soldering
First, you have to tear down the Ikea device. 
User @oleksiikutuzov provided great pictures to do so: https://github.com/oleksiikutuzov/IKEA-VINDSTYRKA/blob/main/teardown.md

I HIGHLY suggest to unpin the display connector and to unscrew the PCB completly before soldering.

This is the PCB inside, I marked each connection point you could need:

<img src="Images/PCB.jpeg" width="500px">

Specifically, you need to solder 4 jumpers:
- Vcc (5V or 3V depending on your microcontroller supply voltage)
- GND (ground)
- SDA (one of the two pins to perform the I2C connection)
- SCL (the other pin to perform the I2C connection)


If you do not want to risk the PCB, you can also opt to cut the cables running from the PCB to the sensor and connecting the jumpers to them, while also resoldering them.


### step 2: connect your microcontroller
You can now connect your microcontroller, DSA and SCL are the two I2C protocol wires.
The DSA and SCL corresponds to pins specific to the board your using. 
For example, the Esp8266 Nodemcu has as default pins D1 and D2.
You can easily find them by googling "xxxxx board I2C default pins".

This git also provides the script to upload to the microcontroller using the Arduino IDE.
It has to be 

## Things to do

- esp sleep instead of delay to save power
- better webpage user experience
- fix the upload time (e.g. at xx:00)

- connection to google home ( ? )

## Acknowledgements

I want to thankyou @XXXX for the teardown that showed the possiblity to connect a microcontroller,
  @senserison to build a really good sensor 
@ikea to encapsuledet it in a economical good lookkig piece. 

