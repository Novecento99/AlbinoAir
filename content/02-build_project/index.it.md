+++
archetype = "chapter"
title = "Assemblaggio"
weight = 2

+++

## Come costruire questo progetto

### fase 1: smontaggio

Per prima cosa, dovete smontare il dispositivo Ikea. Fate attenzione e fatelo con molta attenzio, è facile che si rovini (come è successo al mio primo tentativo). L'utente [@oleksiikutuzov](https://github.com/oleksiikutuzov) ha fornito ottime immagini per farlo, potete seguire il suo tutorial qui: https://github.com/oleksiikutuzov/IKEA-VINDSTYRKA/blob/main/teardown.md

Riporterò qui alcuni passaggi solo per completezza:

### passo 2: saldatura

Suggerisco vivamente di staccare il connettore del display e di svitare completamente il PCB prima di saldare in questo modo:

// inserire le foto qui

Questi sono i relativi pin disponibili:

![](PCB.jpeg)

In particolare, è necessario saldare 4 fili:

- Vcc (5V o 3V a seconda della tensione di alimentazione del microcontrollore)
- GND (massa)
- SDA (uno dei due pin per eseguire la connessione I2C)
- SCL (l'altro pin per eseguire la connessione I2C)

Se non volete rischiare il PCB, potete anche scegliere di tagliare i cavi che vanno dal PCB al sensore e saldare dei ponticelli su di essi "dirottandoli" dai cavi stessi. Questo è il mio primo tentativo (disordinato) per esempio:

// foto qui

### passo 3: collegare il microcontrollore e testare la connessione

4 fili: collegare Vcc e Ground rispettivamente ai pin corretti per alimentare il micro, mentre DSA e SCL sono i due fili del protocollo I2C: DSA e SCL corrispondono ai pin specifici della scheda in uso.

Potete trovarli facilmente cercando su Google "yourbard I2C default pins". Eccone alcuni:

| **Scheda** | **SDA** | **SCL** |
| ----------- | ------- | ------- |
| ESP32 WROOM | GPIO21 | GPIO22 |
| Arduino Uno | A4 | A5 |
| D1 Mini | GPIO4 | GPIO5 |

Ora, è necessario scaricare e installare ([Arduino IDE](https://www.arduino.cc/en/software)) e, attraverso il gestore delle librerie di Arduino, la libreria thingspeak. E installate aggiungendo come zip le ultime versioni di XXX e XXX (quando ho fatto questo git le ultime versioni erano rispettivamente YY e ZZ).

Caricatela sul vostro microcontrollore e collegatela al vostro Ikea Vindistrka.

Se riuscite a leggere i dati sul monitor seriale (fate attenzione a impostare il baudrate corretto), siete pronti a caricare i dati nel cloud.

### passo 4: caricare i dati nel cloud

Prima di tutto, è necessario creare un canale su ThingSpeak.com in cui caricare i dati.

È possibile creare un canale, dando al canale un nome come "Nuvolino - tuacittà".

Andare su Canali-> creare un nuovo canale. 8 campi con questo ordine:

- PM1.0
- PM2.5
- PM4.0
- PM10.0
- Umidità
- Temperatura
- tVOC
- Stato di Nuvolino

### passo 4: caricare i dati nel cloud

Prima di tutto, è necessario creare un canale su ThingSpeak.com in cui caricare i dati.

È possibile creare un canale, dando al canale un nome come "Nuvolino - yourCity".

Andare su Canali-> creare un nuovo canale. 8 campi con questo ordine:

- PM1.0
- PM2.5
- PM4.0
- PM10.0
- Umidità
- Temperatura
- tVOC
- Stato di Nuvolino

Premete Salva canale e verrete portati alla visualizzazione corrente del vostro nuovo canale. Andare alla scheda Chiavi API e trovare la chiave API di scrittura. Sarà necessario inserirla nello sketch per poter scrivere sul canale.

Scaricare da questo git il file XXXX.ino e configurare le istruzioni di partenza: --> codice

Aprite il vostro canale e potrete vedere i dati aggiornati in tempo reale nella vista del canale. È anche possibile visualizzare indicatori e numeri utilizzando le funzioni widget di thingspeak.

### passo 5: creare un sito web

Per creare un sito web è sufficiente scaricare l'index.html in questo git e sostituire gli iframe con quelli che si possono facilmente prendere dal proprio canale thingspeak.

Quindi, caricare l'index.html in un progetto github (o clonare questo) e andare in impostazioni->XXXX. A questo punto è possibile mettere online il proprio sito web con un semplice clic.

