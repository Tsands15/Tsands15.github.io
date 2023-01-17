---
title: "Syringe Pump"
excerpt: "This automatic syrige pump deleivers precise amounts of fluid at the push of a button!"
header:
  image: /assets/img/LF3DP-Banner-2.jpg
  teaser: /assets/img/Large-Format-3D-Printer-Thumbnail.png
gallery:
  - image_path: assets/img/Slide-3.png
  - image_path: assets/img/Slide-2.png
  - image_path: assets/img/Slide-4.png
   
---

# Features


* **Compatible for syringes of different diameters.** This syringe pump is based off a two-layer design. Each layer has three main components: a plunger holder, a back barrel stabilizer, and a front barrel stabilizer. The plunger holder secures the back plunger of each syringe by allowing it to slot into the holder, supporting it for both forward and backward actuation. The back barrel stabilizer allows the back barrel of each syringe to slot into the holder in a similar fashion, holding the back barrel of the syringe in place so that the plunger is able to move forwards and backwards. The front barrel stabilizer holds the tip of the syringe in place, providing further stability to the syringe as the plunger moves.
* **Easily readable UI.** An LCD display is mounted on the side of the box that displays the flow rate of the syringe pump as well as the time remaining until the syringe is fully empty. There are three buttons mounted on the front of the box: Start, Forward, and Reverse. The syringe pump pushes at the designated flowrate when the start button is pressed. The forward and reverse buttons are used to calibrate the position of the plunger holder for loading the syringe such that the user does not need to manually turn the lead screw. The flow rate can be adjusted by turning the potentiometer dial mounted on the box lid. An RGB LED is also mounted on the box and displays green when the pump is active, yellow when paused, red when the limit switch is triggered, purple when moving in reverse, and blue when moving forward.
* **Arduino was used to implement code.** The Arduino was programmed using an Arduino Mega microcontroller. All components of the syringe pump were first instantiated - the motor, buttons, LEDs, potentiometer, and LCD. Calculations for controlling the step rate of the motor in steps/second based on the desired input flow rate in mL/min were then programmed in for both the large and small syringes. 

# CAD Model
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH35dfcQT936092f0e430b83a7ea45015764?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>

{% include gallery caption="Large Format 3D Printer Gallery" %}
