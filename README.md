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
 
* Soldering iron × 1
 
* Screwdriver × 1
 
* Swiss Army knife 
(it's pretty useful to drill hole or cut stuff)
 
* 5mm 1/2 PP Hollow Sheet Corrugated Plastic Board × 1
 
* Box cutter × 1
 
* Plastic pieces(serve the funtion of a flange)

* Female/Female Jumper Wires

## Building structure

reference:</br>
https://www.hackster.io/hackershack/raspberry-pi-motion-tracking-gun-turret-77fb0bI </br> https://www.youtube.com/watch?v=HoRPWUl_sF8

Since I don't have proper tools to processing fibreboard, I eventually choose PP Hollow Sheet Corrugated Plastic Board to build by main structure.

## Install Guide

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
