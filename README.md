# AtrivaTECH_PicUNO-mpy
Micropython board library with special functions and variables for PicUNO

## Built-In Modules
1) board<br>
   a) lvlset()<br>
     Sets Level shifted GPIOs LOW since they stay high always. Best used at start of program.<br>
   b) LED_BUILTIN [variable]<br>
     Sets GPIO 14 as output with machine.pin and can be used to manipulate inbuilt LED Directly with LED_BUILTIN.value(0/1)<br>
2) Neopixel<br>
   Based on Adafruit's Neopixel library for thr neopixels for micropython which can be used to control neopixels. No extra library required.

### Sample usage:
1) Neopixel module:<br>

   <!-- HTML generated using hilite.me -->
<div style="background: #111111; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%"><span style="color: #fb660a; font-weight: bold">import</span> <span style="color: #ffffff">time</span>
<span style="color: #fb660a; font-weight: bold">from</span> <span style="color: #ffffff">picuno</span> <span style="color: #fb660a; font-weight: bold">import</span> <span style="color: #ffffff">Neopixel</span>
 
<span style="color: #ffffff">numpix</span> <span style="color: #ffffff">=</span> <span style="color: #0086f7; font-weight: bold">30</span>
<span style="color: #ffffff">pixels</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">Neopixel(numpix,</span> <span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">17</span><span style="color: #ffffff">,</span> <span style="color: #0086d2">&quot;GRB&quot;</span><span style="color: #ffffff">)</span>
 
<span style="color: #ffffff">yellow</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">(</span><span style="color: #0086f7; font-weight: bold">255</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">100</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">)</span>
<span style="color: #ffffff">orange</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">(</span><span style="color: #0086f7; font-weight: bold">255</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">50</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">)</span>
<span style="color: #ffffff">green</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">(</span><span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">255</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">)</span>
<span style="color: #ffffff">blue</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">(</span><span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">255</span><span style="color: #ffffff">)</span>
<span style="color: #ffffff">red</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">(</span><span style="color: #0086f7; font-weight: bold">255</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">)</span>
<span style="color: #ffffff">color0</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">red</span>
 
<span style="color: #ffffff">pixels.brightness(</span><span style="color: #0086f7; font-weight: bold">50</span><span style="color: #ffffff">)</span>
<span style="color: #ffffff">pixels.fill(orange)</span>
<span style="color: #ffffff">pixels.set_pixel_line_gradient(</span><span style="color: #0086f7; font-weight: bold">3</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">13</span><span style="color: #ffffff">,</span> <span style="color: #ffffff">green,</span> <span style="color: #ffffff">blue)</span>
<span style="color: #ffffff">pixels.set_pixel_line(</span><span style="color: #0086f7; font-weight: bold">14</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">16</span><span style="color: #ffffff">,</span> <span style="color: #ffffff">red)</span>
<span style="color: #ffffff">pixels.set_pixel(</span><span style="color: #0086f7; font-weight: bold">20</span><span style="color: #ffffff">,</span> <span style="color: #ffffff">(</span><span style="color: #0086f7; font-weight: bold">255</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">255</span><span style="color: #ffffff">,</span> <span style="color: #0086f7; font-weight: bold">255</span><span style="color: #ffffff">))</span>
 
<span style="color: #fb660a; font-weight: bold">while</span> <span style="color: #fb660a; font-weight: bold">True</span><span style="color: #ffffff">:</span>
    <span style="color: #fb660a; font-weight: bold">if</span> <span style="color: #ffffff">color0</span> <span style="color: #ffffff">==</span> <span style="color: #ffffff">red:</span>
       <span style="color: #ffffff">color0</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">yellow</span>
       <span style="color: #ffffff">color1</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">red</span>
    <span style="color: #fb660a; font-weight: bold">else</span><span style="color: #ffffff">:</span>
        <span style="color: #ffffff">color0</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">red</span>
        <span style="color: #ffffff">color1</span> <span style="color: #ffffff">=</span> <span style="color: #ffffff">yellow</span>
    <span style="color: #ffffff">pixels.set_pixel(</span><span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">,</span> <span style="color: #ffffff">color0)</span>
    <span style="color: #ffffff">pixels.set_pixel(</span><span style="color: #0086f7; font-weight: bold">1</span><span style="color: #ffffff">,</span> <span style="color: #ffffff">color1)</span>
    <span style="color: #ffffff">pixels.show()</span>
    <span style="color: #ffffff">time.sleep(</span><span style="color: #0086f7; font-weight: bold">1</span><span style="color: #ffffff">)</span>
</pre></div>

2) board Module: <br>
 <!-- HTML generated using hilite.me --><div style="background: #111111; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%"><span style="color: #fb660a; font-weight: bold">from</span> <span style="color: #ffffff">picuno</span> <span style="color: #fb660a; font-weight: bold">import</span> <span style="color: #ffffff">board</span>
<span style="color: #fb660a; font-weight: bold">import</span> <span style="color: #ffffff">rp2</span>
<span style="color: #fb660a; font-weight: bold">from</span> <span style="color: #ffffff">machine</span> <span style="color: #fb660a; font-weight: bold">import</span> <span style="color: #ffffff">Pin</span>
<span style="color: #fb660a; font-weight: bold">import</span> <span style="color: #ffffff">utime</span>

<span style="color: #ffffff">board.lvlpins()</span>

<span style="color: #fb660a; font-weight: bold">while</span> <span style="color: #fb660a; font-weight: bold">True</span><span style="color: #ffffff">:</span>
    <span style="color: #ffffff">board.LED_BUILTIN.value(</span><span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">)</span>
    <span style="color: #ffffff">utime.sleep(</span><span style="color: #0086f7; font-weight: bold">2</span><span style="color: #ffffff">)</span>
    <span style="color: #ffffff">board.LED_BUILTIN.value(</span><span style="color: #0086f7; font-weight: bold">1</span><span style="color: #ffffff">)</span>
    <span style="color: #ffffff">utime.sleep(</span><span style="color: #0086f7; font-weight: bold">2</span><span style="color: #ffffff">)</span>
    <span style="color: #ffffff">machine.Pin(</span><span style="color: #0086f7; font-weight: bold">2</span><span style="color: #ffffff">,</span> <span style="color: #ffffff">machine.Pin.OUT).value(</span><span style="color: #0086f7; font-weight: bold">1</span><span style="color: #ffffff">)</span>
    <span style="color: #ffffff">utime.sleep(</span><span style="color: #0086f7; font-weight: bold">1</span><span style="color: #ffffff">)</span>
    <span style="color: #ffffff">machine.Pin(</span><span style="color: #0086f7; font-weight: bold">2</span><span style="color: #ffffff">,</span> <span style="color: #ffffff">machine.Pin.OUT).value(</span><span style="color: #0086f7; font-weight: bold">0</span><span style="color: #ffffff">)</span>
    <span style="color: #ffffff">utime.sleep(</span><span style="color: #0086f7; font-weight: bold">1</span><span style="color: #ffffff">)</span>
</pre></div>
