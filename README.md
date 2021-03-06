Arduino-LMIC-v1.5 library
=========================
This repository contains the IBM LMIC (LoraMAC-in-C) v1.5 library, 
slightly modified to run in the Arduino environment, allowing using 
the Semtech SX1272/SX1276 or HopeRF RFM92/95 LoRa tranceiver with 
an Arduino.

The HAL has been imported from Matthijs Kooijman's adaptation of
LMIC v1.4 [https://github.com/matthijskooijman/arduino-lmic], as well
as some modifications in the library itself.

This repository is work-in-progress.

This library uses most of the storage space from an ATmega328 based 
Arduino (UNO for example) and is therefore not very usable on these platform.
It has been tested on Teensy 3.1 and Teensy LC.

Connections
-----------
Note that the SX1272/SX1276 and RFM92/95 modules run at 3.3V and do 
not like 5V on its pins, so make sure to use a level shifter, or an 
Arduino running at 3.3V.

The pins to use are shown (and can be changed) in the pinmap in example
.ino files. 

For the HopeRF RFM92/RFM95:
Connecting RST is needed. The txrx pin is not used.

For the SX1272/SX1276: 
It seems that connecting RST is not needed, and RXTX output on the Arduino 
side (which controls the RX/TX antenna switch) can be connected to the 
antenna switch (pin FEM_CTX on the evaluation board). Alternatively, you 
can connect the RXTX pin of the SX1272 directly to the antenna switch (by 
connecting RXTX and FEM_CTX together on the evaluation board, or moving 
R2 to R1). I'm not sure why you wouldn't always want this connection to 
be made, but apparently there is a reason to control the switch from the 
Arduino instead of from the SX1272.

License
-------
The source files in this repository are made available under the Eclipse
Public License v1.0, except for the examples which use a more liberal
license. Refer to each individual source file for more details.
