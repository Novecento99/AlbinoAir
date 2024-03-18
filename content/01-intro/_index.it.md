+++
archetype = "chapter"
title = "Dispositivo Ikea"
weight = 1
+++

## Il dispositivo

Questo progetto accede ai dati grezzi del sensore di qualità dell'aria Ikea **VINDSTYRKA** e li invia ai canali di [Thingspeak](https://thingspeak.com/), per poi visualizzarli nella homepage di questo sito.

![](ikea.jpeg)

Per realizzare il progetto, sono necessari:

- un microcontrollore (come ESP32, ESP8266 o un D1 Mini)
- alcuni ponticelli per saldare il micro al sensore
- abilità di base nella saldatura
- cacciaviti: le viti esterne sono ad esagono incassato, mentre quelle interne sono le classiche phillips
- un account thingspeak (gratuito)

Il VINDSTYRKA di Ikea si basa sul sensore SEN54, che è la scelta migliore per la sua classe di prezzo. Garantisce una buona precisione per oltre 10 anni. Misura PM1.0, PM2.5, PM4.0, PM10.0 (questi ultimi due con una precisione inferiore rispetto agli altri due), temperatura, umidità e tvoc.

[Sensirion SEN54](https://sensirion.com/products/catalog/SEN54/)
