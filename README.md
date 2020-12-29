This project provides readings from several ICs from an IBM 5160 motherboard. The information here is to be useed for diagnostics. It allows you to compare to a working 5160 motherboards and hopefully narrow down the IC that is causing the problem.

The data has been recorded with an AZ-Delivery Logic Analyzer. It is a cheap clonning of the Saleae Logic Analyser. How it works:

- youn need to have an 8/16 bit clonning of Saleae
- you need to download the Logic 2 software from Saleae
- you need to make the recordings of the same pins used in my own recordings
- compare the results with your working or faulty motherboard

It is known what the BIOS chip is supposed to output once the computer is powered on. The analyzer(or plugin) "Simple Parallel" is used. This plugin requires a "clock" even if in theory one is not needed.

### BIOS U18

Only 4 pins are recorded instead of all the 8 pins.

Configuration:
- The tested PINS are: CPU reset, /OE, Q4, Q5, Q6, Q7 (named also D4, D5 ...)
- In the simple parallel port plug-in the pins are ordered : Q4, Q5, Q6, Q7
- In the simple parallel port plug-in the /OE is used as "clock" with clock state "Rising Edge".

Results:
The Simple Parallel plugin outputs these bytes for pins Q4 - Q7. The result looks like this (these are only Q4-Q7):

- Simple Parallel	data 0x0
- Simple Parallel	data 0xE
- Simple Parallel	data 0x5
- Simple Parallel	data 0xE
- Simple Parallel	data 0x0
- Simple Parallel	data 0xF
- Simple Parallel	data 0x3
- Simple Parallel	data 0xF
- Simple Parallel	data 0xB

### Pins S0, S1, S2 on CPU 8088 
5 pins are read.

### Versions:
- Logic 2.3.16
- IBM motherboard 256-640 KB, 1983 - 1986

### Resources:
Saleae forum: https://discuss.saleae.com/
Info about 8088: https://www.geeksforgeeks.org/pin-diagram-8086-microprocessor/
