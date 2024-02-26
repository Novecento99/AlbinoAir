# AlbinoAir

this projects aims to access the Ikea VINDSTYRKA air quality sensor raw data. 
To do so, a microcontroller (such as Arduino or Esp32) is used.

resulting website (aestetichs greatly improvable): https://novecento99.github.io/AlbinoAir/


## Build this project

First, you have to tear down the device. 
User @oleksiikutuzov provided great pictures about it: https://github.com/oleksiikutuzov/IKEA-VINDSTYRKA/blob/main/teardown.md

You need to solder 4 jumpers:
- Vcc (5V or 3V depending on your microcontroller supply voltage)
- GND
- SDA
- SCL

<img src="images/PCB.jpeg" width="500px">




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
