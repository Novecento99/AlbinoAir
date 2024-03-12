# AlbinoAir

WORK IN PROGRESS 

this projects accesses the Ikea VINDSTYRKA air quality sensor raw data and send them to thingspeak channels, which can therefore visualized in a comprehnsive website (e.g. https://novecento99.github.io/Nuvolino/) (yeah I'm not good at making websites). 

<img src="Images/ikea.jpeg" width="500px">

To do so, you will need:
- a microcontroller (such as ESP32, ESP8266 or a D1 Mini)
- some jumpers
- basic soldering skills
- screwdriver (type XXXX): You will need a long Torx T6 for outer screws, Philips 2.0 for the inner frame and Philips 1.5 for PCB screws

The Ikea VINDSTYRKA is based on the SEN54 sensor, which is the top choice for its price class. Providing good accuracy for 10+ years.
https://sensirion.com/products/catalog/SEN54/


## How to build this project


### step 1: teardown 
First, you have to tear down the Ikea device. 
User @oleksiikutuzov provided great pictures to do so: https://github.com/oleksiikutuzov/IKEA-VINDSTYRKA/blob/main/teardown.md

I HIGHLY suggest to unpin the display connector and to unscrew the PCB completly before soldering like this:

This is the PCB inside, I marked each connection point you could need:

<img src="Images/PCB.jpeg" width="500px">

Specifically, you need to solder 4 lo:
- Vcc (5V or 3V depending on your microcontroller supply voltage)
- GND (ground)
- SDA (one of the two pins to perform the I2C connection)
- SCL (the other pin to perform the I2C connection)


If you do not want to risk the PCB, you can also opt to cut the cables running from the PCB to the sensor and soldering jumpers to them "hijacking" from the cables itself.

### step 2: soldering
### step 3: connect your microcontroller

4 wires: connect Vcc and Ground respectively to the correct pins to power your micro, while DSA and SCL are the two I2C protocol wires: the DSA and SCL corresponds to pins specific to the board your using. 

For example, the Esp8266 Nodemcu has as default pins D1 and D2.
You can easily find them by googling "xxxxx board I2C default pins".

This git provides the script (xxxxx.ino) to upload to the microcontroller using the Arduino IDE.

There are two versions: one doesn't need internet connection and can be useful to perform tests. 
It just reads data from the sensor and display it on the serial connection.


If you can read the data on the serial, you are ready to upload in cloud

### step 4: upload data to the cloud

Upload the .ino file and you are to go to connect your microcontroller to the IKEA thing.
You need to set some parameters in the file: 


### step 5: deploy a website





## Things to do
- channel to upload number of resets DONE
- find a name to it
- esp sleep instead of delay to save power, currently a delay(600000) (lol) it's implemented
- better webpage and graphs 
- set a fixed upload time (e.g. at xx:00)

- a connection to google home would be very cool

## Acknowledgements

I want to thankyou @XXXX for the teardown that showed the possiblity to connect a microcontroller,
  @senserison to build a really good sensor
@ikea to encapsuledet it in a economical good lookkig piece and @olazzari to help with everything.

