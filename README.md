# Nuvolino

WORK IN PROGRESS 

this projects accesses the Ikea VINDSTYRKA air quality sensor raw data and send them to thingspeak channels, which can therefore visualized in a comprehnsive website (e.g. https://novecento99.github.io/Nuvolino/) (yeah I'm not good at making websites). 

<img src="Images/ikea.jpeg" width="500px">

To do so, you will need:
- a microcontroller (such as ESP32, ESP8266 or a D1 Mini)
- some jumpers to solder your micro to the sensor
- basic soldering skills
- screwdrives: the outer screws are heaxagon, while the inner ones are classical phillips
- a (free) thingspeak account


The Ikea VINDSTYRKA is based on the SEN54 sensor, which is the top choice for its price class. Providing good accuracy for 10+ years. It measure PM1.0, PM2.5, PM4.0, PM10.0 (these last two with less accuracy then the other two.), temperature humidity and tvoc.

https://sensirion.com/products/catalog/SEN54/


## How to build this project


### step 1: teardown 
First, you have to tear down the Ikea device. Be careful and do it with patience it's easy to ruin it (as my first try went). 
User @oleksiikutuzov provided great pictures to do so, you can follow their tutorial: https://github.com/oleksiikutuzov/IKEA-VINDSTYRKA/blob/main/teardown.md

I'm going to report here some steps just for completation:





### step 2: soldering

I HIGHLY suggest to unpin the display connector and to unscrew the PCB completly before soldering like this:

// insert photos here


Those are the relevant pins available:

<img src="Images/PCB.jpeg" width="500px">

Specifically, you need to solder 4 wires:
- Vcc (5V or 3V depending on your microcontroller supply voltage)
- GND (ground)
- SDA (one of the two pins to perform the I2C connection)
- SCL (the other pin to perform the I2C connection)


If you do not want to risk the PCB, you can also opt to cut the cables running from the PCB to the sensor and soldering jumpers to them "hijacking" from the cables itself. This is my (messy) first try for example:

// photo here

### step 3: connect your microcontroller and test the connection

4 wires: connect Vcc and Ground respectively to the correct pins to power your micro, while DSA and SCL are the two I2C protocol wires: the DSA and SCL corresponds to pins specific to the board your using. 

For example, the Esp8266 Nodemcu has as default pins D1 and D2.
You can easily find them by googling "xxxxx board I2C default pins".

This git provides the script (xxxxx.ino) to upload to the microcontroller using the Arduino IDE.

There are two versions: one doesn't need internet connection and can be useful to perform tests. 
It just reads data from the sensor and display it on the serial connection.


If you can read the data on the serial monitor (beware to set the correct baudrate), you are ready to upload in cloud

### step 4: upload data to the cloud 

First of all, you need to make an account on thingspeak. The account is free. Make a new channel with 8 fields.


Download from this git the XXXX.ino and configure the starting istructions:
--> code 



Upload the XXXXX.ino file and you are done! open your channel, you will be able to see the data updated in real time in the channel view. You can also make gauges and numbers display by using the widget functions of thingspeak

### step 5: deploy a website
to make a website you just need to download the index.html in this git and substitute the iframes with the ones that you can easily take from your thingspeak channel

Then, upload the index.html in a github project (or just clone this one) and go to settings->XXXX. There you can take your website online with a simple click. 

more info here: 


## Things to do
- Unmarry from thingspeak, an open source method would be better
- channel to upload number of resets DONE
- find a name to it
- esp sleep instead of delay to save power, currently a delay(600000) (lol) it's implemented
- better webpage and graphs 
- set a fixed upload time (e.g. at xx:00)

- a connection to google home would be very cool
- translations ?

## Acknowledgements

@olazzari for the endless utility provided

