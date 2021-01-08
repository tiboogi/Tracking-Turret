# CheaperTrackingTurret
This is my school project implementing https://github.com/HackerShackOfficial/Tracking-Turret project in a cheaper way
by using cheaper material to build as well as modify some parts.

## Materials
reference:</br>https://www.hackster.io/hackershack/raspberry-pi-motion-tracking-gun-turret-77fb0bI

* electric airsoft gun × 1(in my case it's an UZI) 

* Raspberry Pi 3 Model B × 1

* any webcam with USB head × 1(in my case it's Ebook W15)
 
* Adafruit DC+Stepper Motor HAT For RPi × 1
 
* NEMA 17 Stepper Motor, 200 Steps/Rev × 2
 
* Tolako 5v Relay Module × 1</br>
(in my case I got a defect airsoft gun that can't fire properly, so I use a buzzer to test the signal instead of Single Relay)
 
* Yeeco 1A DC to DC Step Up Converter
 
* Tape × 1
 
* Portable Cell Phone Charger × 1
 	
* USB-A to Micro-USB Cable × 1
 	
* Solder × 1
 
* Soldering Iron × 1
 
* Screwdriver × 1
 
* Swiss Army Knife 
(it's pretty useful to drill hole or cut stuff)
 
* 5mm 1/2 PP Hollow Sheet Corrugated Plastic Board × 1
 
* Box Cutter × 1
 
* Some Plastic pieces(serve the funtion of a flange)

* Female/Female Jumper Wires

* Male/Female Jumper Wires
## Building structure

reference:\
https://www.hackster.io/hackershack/raspberry-pi-motion-tracking-gun-turret-77fb0bI </br> video: \
https://www.youtube.com/watch?v=HoRPWUl_sF8

Since I don't have proper tools to processing fibreboard, I eventually choose PP Hollow Sheet Corrugated Plastic Board to build by main structure.

### Base

First off, trace out two 15-cm diameter circles with a compass and cut them out using box cutter from your hollow sheet. \
<img src="https://i.imgur.com/nM8NEM2.jpg" alt="" class="" data-position="1616" style="max-width:50%;" >

Drill a hole in center and tape the stepper motor on it.

If you didn't subscribe Author's patreon, you can cut out few more pieces to make flange instead of using 3D printer \
<img src="https://i.imgur.com/39TgXZR.jpg" alt="" class="" data-position="1616" width:50%;" >
<img src="https://i.imgur.com/tOuY76H.jpg" alt="" class="" data-position="1616" width:50%;" >
### Legs
Cut out 2 leg base on airsoft gun's height，drill hole at about gun's gravity center and tape it all

<img src="https://i.imgur.com/vlCcqhE.jpg" alt="" class="" data-position="1616" style="max-width:50%;" >


### Wire the gun

Before moving onto the next step, prepare your airsoft gun so it is ready to be mounted onto the turret when it is built. The method of preparation depends on your airsoft or nerf gun model, but there are two options the Author found for attaching wires to our gun:

Option 1:

The first, but perhaps more difficult option, is to take apart your gun and find the switch that gets closed when the trigger is pulled. Remove the wires from this switch and solder them directly to your own longer power and ground wires and feed them out of the gun. Then reassemble the gun. The physical switch actuated by the trigger that you just disconnected will later be replaced by an electrical relay controlled by the Raspberry Pi. Although we used this option, we found it extremely difficult to reassemble our gun properly.

Option 2:

The second option is to leave your gun intact, but solder the power and ground wires to the electrical contacts of the batteries instead. You will then have to hold the trigger down using tape or other means so that the internal switch is closed.

Option 3:(mycase)

IF your gun can't fire properly simply use a buzzer to test
<img src="https://i.imgur.com/fn46NmV.jpg" alt="" class="" data-position="1616" style="max-width:50%;" >

### Electronic stuff
Wire your stepper moter to HAT(skip the GND) ![](https://i.imgur.com/uTD4yFA.jpg=60%x)

Connect the relay to the stepper motor hat by connecting the power and ground of the relay to the power rail of the stepper motor hat (red and purple wires in the picture below). Then connect the signal wire to the GPIO pin 22 on the Pi (orange wire in the picture below). Connect the output of the relay to the wires on your gun.
![](https://i.imgur.com/4behgOw.jpg=60%x)




## Softer Install Guide

Make sure pip is installed. 
```bash
sudo apt-get install python pip
```

Setup I2C on your Raspberry Pi

https://learn.adafruit.com/adafruits-raspberry-pi-lesson-4-gpio-setup/configuring-i2c

Install the Adafruit stepper motor HAT library.

```bash
sudo pip install git+https://github.com/adafruit/Adafruit-Motor-HAT-Python-Library
```

Install OpenCV 3. Follow all steps for python 2.7 instructions

http://www.pyimagesearch.com/2016/04/18/install-guide-raspberry-pi-3-raspbian-jessie-opencv-3/

Make sure to create your virtual environment with the extra flag.

```bash
mkvirtualenv cv --system-site-packages -p python2
```

Source your bash profile

```bash
source ~/.profile
```

Activate your virtual environment

```
workon cv
```

Clone this repository

```
git clone git@github.com:HackerHouseYT/Tracking-Turret.git
```

Navigate to the directory

```
cd Tracking-Turret
```

Install dependencies to your virtual environment

```
pip install imutils RPi.GPIO
```

Run the project!

```
python turret.py
```

## Setting Parameters

turret.py has a couple parameters that you can set.

```python
### User Parameters ###

MOTOR_X_REVERSED = False
MOTOR_Y_REVERSED = False

MAX_STEPS_X = 30
MAX_STEPS_Y = 15

RELAY_PIN = 22

#######################
```

These will be located at the top of the file. Use `vim turret.py` to open the file. Press `i` to edit.
Once you've made your changes, press `esc` then `ZZ` to save.
