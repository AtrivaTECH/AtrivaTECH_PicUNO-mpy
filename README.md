# AtrivaTECH_PicUNO-mpy
Micropython board library with special functions and variables for PicUNO

## Built-In Modules
1) board<br>
   a) lvlset()<br>
     Sets Level shifted GPIOs LOW since they stay high always. Best used at start of program.<br>
   b) LED_BUILTIN [variable] <br>
     Sets GPIO 14 as output with machine.pin and can be used to manipulate inbuilt LED Directly with LED_BUILTIN.value(0/1)<br>
2) Neopixel<br>
   Based on Adafruit's Neopixel library for thr neopixels for micropython which can be used to control neopixels. No extra library required.

## Installation
Download the picuno.py file from <a href="https://github.com/atulravi/AtrivaTECH_PicUNO-mpy/tree/main/picuno">/picuno</a> and upload it to the root folder of your PicUNO via the file manager in Thonny. Then use the below method at the start of the program to import the library.

```
from picuno import board
```


### Sample usage:
1) Neopixel module:<br>

``` import time
from picuno import Neopixel
numpix = 30
pixels = Neopixel(numpix, 0, 17, "GRB")


yellow = (255, 100, 0)
orange = (255, 50, 0)
green = (0, 255, 0)
blue = (0, 0, 255)
red = (255, 0, 0)
color0 = red


pixels.brightness(50)
pixels.fill(orange)
pixels.set_pixel_line_gradient(3, 13, green, blue)
pixels.set_pixel_line(14, 16, red)
pixels.set_pixel(20, (255, 255, 255))


while True:
	if color0 == red:
		color0 = yellow
		color1 = red
	else:
		color0 = red
		color1 = yellow
	pixels.set_pixel(0, color0)
	pixels.set_pixel(1, color1)
	pixels.show()
	time.sleep(1)
```


2) board Module: <br>
```
from picuno import board
import rp2
from machine import Pin
import utime


board.lvlpins()


while True:
	board.LED_BUILTIN.value(0)
	utime.sleep(2)
	board.LED_BUILTIN.value(1)
	utime.sleep(2)
	machine.Pin(2, machine.Pin.OUT).value(1)
	utime.sleep(1)
	machine.Pin(2, machine.Pin.OUT).value(0)
	utime.sleep(1)
```
## Credits
Code maintained by Atul Ravi-Founder Atrivatech P Ltd <br>
Special Thanks to CodeItDoIt on GitHub for the addition of comments. 
