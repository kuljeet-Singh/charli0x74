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
Approximate budget required for this project is $250. Bills and and links to suppliers can be seen [here](https://github.com/kuljeet-Singh/charli0x74/tree/master/Documents/INVOICES). Since all these sensors(or effectors)were ordered in groups,we saved a good amount of money on shipping. If you are alone working on this project you should be ready to spend more money!
![capture2](https://user-images.githubusercontent.com/43182173/49831390-c85d1a80-fd61-11e8-996f-b08adfee345e.PNG)

## Time Commitment
This project can be completed in 3 days.(Required all parts and neccessary tools are already in hand).Sometimes it may take only 2 days where as sometimes it takes more than a month to ship the product.Generally, it should take around 7-8 hours to finish (taking into account that the PCB has been printed effectively, generally the PCB should take about a half-day to be printed).
The major steps in the process are:


- [Raspberry Pi and Noops installation](#Raspberry-Pi-initialisation-and-Image-creation) (2.5 hours)


- [Other Installations, Connections and Verifications](#Other-Installations,-Connections-and-Verifications) (2 Hours)<br>

- [Soldering](#Soldering) (1.5 Hours)<br>

- Case printing  (30 mins)<br>

- Compiling everything into one project (1 hour)<br>

- Final Test (10 mins)

## Mechanical Assembly

### Raspberry Pi initialisation and Image creation

- Format the [micro-SD card](https://www.raspberrypi.org/learning/software-guide/)
- Download the latest version of [**NOOBS** OS](https://www.raspberrypi.org/downloads/noobs/) 
- Downloading the software takes a while. Click on the link for step by step [video](https://www.raspberrypi.org/help/videos/#noobs-setup) to flash the image of OS to your micro-SD card.
- When downloading is done connect your Raspberry Pi to a screen and plug amouse and keyboard to it.
- Once setup is done, just enable I2C,VNC and SSH interfaces. This can be done by selecting *Preference* from *Start Menu* and then clicking *Raspberry Pi configuration* and then select *Interfaces* and now set I2C, SSH and VNC to enable mode.

### Other Installations, Connections and Verifications
1) Here's the Raspberry Pi wired to with I2C:  
- 3V3 to sensor VIN
- GND to sensor GND
- SCL to sensor SCL
- SDA to sensor SDA
<br>
The connections should look like this:

![captur2e](https://user-images.githubusercontent.com/43182173/49890302-c5b9fe00-fe11-11e8-81bb-9fd9f096e119.PNG)

2) Checking for I2C address:

```
sudo i2c detect -y 1
```

If this address is not visible check connections again. 
![capture4](https://user-images.githubusercontent.com/43182173/49890633-8f30b300-fe12-11e8-9b6a-38004896c174.PNG)

Once I2C is detected we are ready for next step.<br>Now intall and update python libraries on Raspberry Pi. You can obtain a file providing step to step assistance [here](https://github.com/kuljeet-Singh/charli0x74/blob/master/Python%20Files.docx) 

<br>

Once its all done now run athe following command:

```
sudo pip3 install adafruit-circuitpython-is31fl3731
```
<br>

Now create a new file using nano editor by name it  as a ".py" file as you you did earlier and write following code into it:

```
import board
import busio
import adafruit_is31fl3731
display = adafruit_is31fl3731.Matrix(i2c)
```
When the display initializes it will go through and clear each frame (there are 8 frames total) of the display. You might
see the display momentarily flash and then turn off to a clear no pixel lit image.<br>
You can control all of the board's pixels using the fill function. Send to this function a value from 0 to 255 where 0 is
every LED pixel turned off and 255 is every LED pixel turned on to maximum brightness. For example to set all the
pixels to half their brightness run:

```
display.fill(127)
```
It will give an output like this:
![capture7](https://user-images.githubusercontent.com/43182173/49893545-acb54b00-fe19-11e8-966f-d723d20c216e.PNG)

<br>
Now for some fun! You can set any of the LED pixels using the pixel function. This function takes the following
parameters:<br>
- X position - The location of the horizontal / X pixel position.<br>
- Y position - The location of the vertical / Y pixel position.<br>
- Intensity - This is a value from 0 to 255 which specifies how bright the pixel should be, 0 is off and 255 is
maximum brightness. Use an in-between value to show a less bright pixel.<br>

```
display.pixel(0,0,255)
```
![capture8](https://user-images.githubusercontent.com/43182173/49893699-0ddd1e80-fe1a-11e8-9ae9-0cd172238847.PNG)

Frame number - This is the frame number to make the active frame for display or drawing. There are 8 frames
total, 0 through 7.<br>
Show - An optional boolean that defaults to True and specifies if the frame should be immediately displayed
(True) or just made active so that pixel and fill commands draw on it but it's not yet shown.<br>
For example to clear frame 1 and draw a few pixels on it, then display it you can run:<br>

```
display.frame(1)
```
A full sample code can be downloaded [here](https://github.com/kuljeet-Singh/charli0x74/blob/master/board.py)
### Soldering

1) Soldering the LED's matrix and driver **together**. This is required before any further step.

![1](https://user-images.githubusercontent.com/43182173/49889616-fdc04180-fe0f-11e8-9232-1da6752eef19.png)






