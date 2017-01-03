# SI4844 FM Radio

This is an FM radio using the digital reciever module ```Si4844```.

- [All About Circuits](http://www.allaboutcircuits.com/projects/build-an-arduino-controlled-am-fm-sw-radio/) - this is the original blog post about setting up radio
- [Design Guide](http://www.silabs.com/Support%20Documents/TechnicalDocs/AN602.pdf)
- [Programming Guide](http://www.silabs.com/Support%20Documents/TechnicalDocs/AN610.pdf)

## STATUS

- [x] Circuit Power
- [x] I2C Communication
- [x] Si4844 power
- [x] FM demodulation
- [x] Basic functionality

To do:
- [ ] Enhanced audio amplifier
- [ ] Enhanced antenna
- [ ] Enclosure


## Build Notes

**Microcontroller** - The original blog post uses an Arduino 3.3v Pro Mini.  I dont have one of these so instead I'm using a Teensy 3.2.  The main reason I'm going with the Teensy is that it's also a 3.3v board.  I've also thought about using a ```3.3v Trinket Pro``` but I dont have my 3.3v-5v serial adapter.  The ```Teensy 3.2``` has built in serial converter.

**Power** - it is suggested to power the whole board from a 3.3v regulator and not the microcontroller as the microcontroller will not supply enough amps.

**Communication** - the ```Si4844``` is an I2C slave device with an address ```0x11```.  The ```Si4844``` maximum speed is 50kHz and during some parts of the startup phase, the speed must not exceed 10kHz.  With Arduino, you can use the ```Wire``` library and change the I2C speed with ```Wire.setClock(10000)``` which sets the I2C clock speed to 10k.  I used 2.2k pullup resistors for both the SDA and SCK lines.

**Audio** - I have a basic mono audio amplifyer circuit.  I will post the link when I find it again.

**Antenna** - The setup works without any 'official' antenna.  I basically have a 6 inch wire twisted once which is providing quality reception.
