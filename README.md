This project provides readings from several ICs from an IBM 5160 motherboard. The information here is to be useed for diagnostics. It allows you to compare to a working 5160 motherboards and hopefully narrow down the IC that is causing the problem.

The data has been recorded with an AZ-Delivery Logic Analyzer. It is a cheap clonning of the Saleae Logic Analyser. How it works:

- youn need to have an 8/16 bit clonning of Saleae
- you need to download the Logic 2 software from Saleae
- you need to make the recordings of the same pins used in my own recordings
- compare the results with your working or faulty motherboard

It is known what the BIOS chip is supposed to output once the computer is powered on. The analyzer(or plugin) "Simple Parallel" is used. This plugin requires a "clock" even if in theory one is not needed. Every componenent has the "clock" configured to a pin that usually chnages when the IC outputs data. Sucha pin is not called "clock", but it does the job. 

### BIOS U18

Only 4 pins are recorded instead of all the 8 pins.

Configuration:
- The tested PINS are: CPU reset, /OE, Q4, Q5, Q6, Q7 (named also D4, D5 ...)
- In the simple parallel port plug-in the pins are ordered : Q4, Q5, Q6, Q7
- In the simple parallel port plug-in the /OE is used as "clock" with clock state "Rising Edge".

Results:
The Simple Parallel plugin outputs these bytes for pins Q4 - Q7
The result looks like this:
name	type	start_time	duration	data
- Simple Parallel	data	2.14607929	0.220641333	    0x0
- Simple Parallel	data	2.36672067	7.91666666e-07	0xE
- Simple Parallel	data	2.3667215	  7.91666666e-07	0x5
- Simple Parallel	data	2.36672233	7.91666667e-07	0xE
- Simple Parallel	data	2.36672317	8.33333334e-07	0x0
- Simple Parallel	data	2.36672404	7.91666667e-07	0xF
- Simple Parallel	data	2.36672488	1.625e-06	      0x3
- Simple Parallel	data	2.36672654	7.91666667e-07	0xF
- Simple Parallel	data	2.36672737	7.91666667e-07	0xB

### Versions:
- Logic 2.3.16
- IBM motherboard 256-640 KB 
