# Building Instructions for Charliplex LED
## Introduction
The IS31FL3731 will let you get back to that classic LED matrix look, with a nice upgrade! This I2C LED driver chip has
the ability to PWM each individual LED in a 16x9 grid so you can have beautiful LED lighting effects, without a lot of
pin twiddling. Simply tell the chip which LED on the grid you want lit, and what brightness and it's all taken care of for
you. <br>

![capture](https://user-images.githubusercontent.com/43182173/49830998-c21a6e80-fd60-11e8-964e-589c806853c4.PNG)

The IS31FL3731 is a nice little chip - it can use 2.7-5.5V power and logic so its flexible for use with any microcontroller.
You can set the address so up to 4 matrices can share an I2C bus. Inside is enough RAM for 8 separate frames of
display memory so you can set up multiple frames of an animation and flip them to be displayed with a single
command.
<br>
This chip is great for making small LED displays, and we even designed the breakout to match up with our ready-to-go
LED grids in red, yellow, green, blue and white. Sandwich the driver and matrix breakout, solder together for a
compact setup. Or you can DIY your own setup, just follow the LED grid schematic in the IS31FL3731 datasheet.

## Budget and Components Required
Approximate budget required for this project is $250. Bills can be seen [here](https://github.com/kuljeet-Singh/charli0x74/tree/master/Documents/INVOICES). Since all these sensors(or effectors)were ordered in groups,we saved a good amount of money. If you are alone working on this project you should be ready to spend more money!
![capture2](https://user-images.githubusercontent.com/43182173/49831390-c85d1a80-fd61-11e8-996f-b08adfee345e.PNG)

## Time Commitment
This project can be completed in 3 days.(Required all parts and neccessary tools are already in hand).Sometimes it may take only 2 days where as sometimes it takes more than a month to ship the product.Generally, it should take around 7-8 hours to finish (taking into account that the PCB has been printed effectively, generally the PCB should take about a half-day to be printed).
The major steps in the process are:
- [Raspberry Pi and Noops installation](*Raspberry Pi initiasation and Image creation)  (2 Hours)<br>
- Verifiaction and Other installations (2 Hours)<br>
- Soldering (1.5 Hours)<br>
- Case printing  (30 mins)<br>
- Compiling everything into one project (1 hour)<br>
- Final Test (10 mins)

## Mechanical Assembly

### Raspberry Pi initiasation and Image creation





