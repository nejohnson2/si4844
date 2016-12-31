# SI4844 FM Radio

This is an FM radio using the digital reciever module ```Si4844```.

## Build Notes

Here are a couple of important links:

- [All About Circuits](http://www.allaboutcircuits.com/projects/build-an-arduino-controlled-am-fm-sw-radio/) - this is the original blog post about setting up radio
- [Si4844 Users Guide](http://www.silabs.com/Support%20Documents/TechnicalDocs/Si4844-B-DEMO.pdf) - this contains the demo schematic and code structure explaination.  There are some slight differencs from the All About Circuit blog

## My Setup

### Microcontroller
The original blog post uses an Arduino 3.3v Pro Mini.  I dont have one of these so instead I'm using a Teensy 3.2.  The main reason I'm going with the Teensy is that it's also a 3.3v board.  I've also thought about using a ```3.3v Trinket Pro``` but I dont have my 3.3v-5v serial adapter.  The ```Teensy 3.2``` has built in serial converter.

**Power** - it is suggested to power the whole board from a 3.3v regulator and not the microcontroller as the microcontroller will not supply enough amps.

**Communication** - the ```Si4844``` is an I2C slave device with an address ```0x11```.  The ```Si4844``` maximum speed is 50kHz and during some parts of the startup phase, the speed must not exceed 10kHz.  I believe the example code will work the same (if you set the Teeny speed to 8MHz).  TWSR is the scalar.  TWBR

i2c_freq = CPU_clock_freq / (16 + (2 * (TWBR) * (Prescalar)))
