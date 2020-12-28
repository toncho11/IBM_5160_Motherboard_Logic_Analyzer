This project provides readings from several ICs from an IBM 5160 motherboard. The information here is to be useed for diagnostics. It allows you to compare to a working 5160 motherboards and hopefully narrow down the IC that is causiong the problem.

The data has been recorded with an AZ-Delivery Logic Analyzer. It is a cheap clonning of the Saleae Logic Analyser. How it works:

- youn need to have an 8/16 bit clonning of Saleae
- you need to download the Logic 2 software from Saleae
- you need to make the recordings of the same pins used in my own recordings
- compare the results with your working or faulty motherboard

It is known what the BIOS chip is supposed to output once the computer is powered on. The analyzer(or plugin) "Simple Parallel" is used. This plugin requires a "clock" even if in theory one is not needed. Every componenent has the "clock" configured to a pin that usually chnages when the IC outputs data. Sucha pin is not called "clock", but it does the job. 

Versions:
- Logic 2.3.16
- IBM motherboard 256-640 KB 
