This repository provides readings from several ICs from an IBM 5160 motherboard. The information here is to be used for diagnostics. It allows you to compare to a working 5160 motherboard and hopefully narrow down the IC that is causing your problem. This repository also contains images and links from http://minuszerodegrees.net. These were stored here for quick reference and backup.

The data has been recorded with an AZ-Delivery Logic Analyzer. It is a [cheap cloning](https://chinese-electronics-products-tested.blogspot.com/p/24m-8ch-logical-analyser-tested.html) of the Saleae Logic Analyser. The clonning should have a 24MS/s sampling rate. How to proceed:

- youn need to have an 8/16 bit clonning of Saleae
- you need to download the Logic 2 software from Saleae
- you need to make the recordings on the same pins for each IC as used in my own recordings
- compare your recordings with the ones prvoided here 


### BIOS U18

The U18 BIOS chip will output the BIOS code once the computer is powered on. Actaully the CPU is reading the BIOS code. The analyzer(or plugin) "Simple Parallel" is used to decode the output of U18. This plugin requires a "clock" even if in theory one is not needed. Only 4 pins are recorded instead of all the 8 pins (Q0-Q7).

Configuration:
- The tested PINS are: CPU reset, /OE, Q4, Q5, Q6, Q7 (named also D4, D5 ...)
- In the simple parallel port plug-in the pins are ordered : Q4, Q5, Q6, Q7 (this is needed for the value reconstriction)
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

It is important if you are reading Q4-Q7 or Q7-Q4. 

### Pins S0, S1, S2 on 8088 CPU
5 pins are read. The 8088 CPU is always in 'maximum' mode meaning that pin 25 is always "S0" and never used as "DEN" pin (see CPU schematics for reference).

The S0,S1,S2 pins represent the following states:

S2 S1 S0 Machine cycle
0 0 0 Interrupt acknowledge
0 0 1 Read I/O port
0 1 0 Write I/O port
0 1 1 Halt
1 0 0 Code access
1 0 1 Read memory
1 1 0 Write memory
1 1 1 Passive

In the beginning 8088 starts a 'Code Access' bus transaction (1,0,0) to read the BIOS ROM U18, so only S2 is HIGH, the others are LOW. 

### Checkpoint codes on 8255A

The IBM 5160 outputs 4 diagnostic codes (3 if everything is OK). The values are "001", "010", "011" and "100". These can be read on the 8255A on the following pins 2, 3, 4 in that direction with names PA2, PA1, PA0. If "100" is shown repeatedly it means a memory error in the first 16 KB (or 64 KB) of memory. The initial state of the 3 pins is first all HIGH and then all LOW.

### Versions:
- Logic 2.3.15
- IBM motherboard 256-640 KB, 1983 - 1986

### Resources:
- IBM 5160 motherboard diagrams: https://ibm.retropc.se/5160/misc/5160_motherboard_diagrams.html
- IBM 5160 start-up sequence: http://minuszerodegrees.net/5160/motherboard/IBM%205160%20-%20Startup%20sequence.htm
- IBM 5160 POST process: http://minuszerodegrees.net/5160/post/5160%20-%20POST%20-%20Detailed%20breakdown.htm
- Saleae forum: https://discuss.saleae.com
- Info about 8088: https://www.geeksforgeeks.org/pin-diagram-8086-microprocessor
- IBM 5160 switches: http://www.minuszerodegrees.net/5160/misc/5160_motherboard_switch_settings.htm
- IBM 5160 RAM on a '64 - 256KB' Type of Motherboard: http://minuszerodegrees.net/5160/ram/5160_ram_64_256.htm
- IBM 5160 RAM on a '256 - 640KB' Type of Motherboard: http://www.minuszerodegrees.net/5160/ram/5160_ram_256_640.htm
- IBM 5160 checkpoints codes: http://www.minuszerodegrees.net/5160/post/5160_post_checkpoint_codes.htm
