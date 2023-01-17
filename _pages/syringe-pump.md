---
title: "Syringe Pump"
excerpt: "This syringe pump delivers precise amounts of fluid at the push of a button!"
header:
  image: /assets/img/LEDscreen.jpg
  teaser: /assets/img/syringepump.jpg
gallery:
  - image_path: assets/img/code.png
   
---

# Features


* **Compatible for syringes of different diameters.** This syringe pump is based off a two-layer design. Each layer has three main components: a plunger holder, a back barrel stabilizer, and a front barrel stabilizer. The plunger holder secures the back plunger of each syringe by allowing it to slot into the holder, supporting it for both forward and backward actuation. The back barrel stabilizer allows the back barrel of each syringe to slot into the holder in a similar fashion, holding the back barrel of the syringe in place so that the plunger is able to move forwards and backwards. The front barrel stabilizer holds the tip of the syringe in place, providing further stability to the syringe as the plunger moves.

* **Arduino was used to implement code.** The Arduino was programmed using an Arduino Mega microcontroller. All components of the syringe pump were first instantiated - the motor, buttons, LEDs, potentiometer, and LCD. Calculations for controlling the step rate of the motor in steps/second based on the desired input flow rate in mL/min were then programmed in for both the large and small syringes. 

## Pump Operation
There are three buttons mounted on the front of the box: Start, Forward, and Reverse. The syringe pump pushes at the designated flowrate when the start button is pressed. The forward and reverse buttons are used to calibrate the position of the plunger holder for loading the syringe such that the user does not need to manually turn the lead screw. The flow rate can be adjusted by turning the potentiometer dial mounted on the box lid. An LCD display is mounted on the side of the box that displays the flow rate of the syringe pump as well as the time remaining until the syringe is fully empty.An RGB LED is also mounted on the box and displays green when the pump is active, yellow when paused, red when the limit switch is triggered, purple when moving in reverse, and blue when moving forward.

## Off the Shelf Parts
| Part | Quantity |
| --- | --- |
| 5 mL Syringe | 1|
| 20 mL Syringe | 1 |
| 1602 LCD | 1 |
| 2040 Aluminum T Slot Framing | 1 |
| Arduino Due | 1 |
| Red Button | 1 |
| Blue Button | 1 |
| Green Button | 1 |
| Breadboard | 1 |
| Flexible Coupler| 1 |
| Knob | 1 |
| Lead Screw | 1 |
| Lead Screw Nut | 1 |
| RGB LED T-1, 5 mm dia. | 1 |
| Limit Switch | 1 |
| Linear Bearing | 1 |
| Nema 17 Stepper Motot | 1 |
| Linear Rod | 2 |
| Potentiometer | 1 |
| RD-65A Power Supply | 1 |
| M3x8 Screw | 20 |
| M3x12 Screw | 8 |

## 3D Printed Parts
| Part | Quantity |
| --- | --- |
| Back Barrel Stabilizer - Lower | 1 |
| Back Barrel Stabilizer - Upper | 1 |
| Box | 1 |
| Front Barrel Stabilizer - Lower | 1 |
| Front Barrel Stabilizer - Upper | 1 |
| Lid | 1 |
| Motor Mount | 1 |
| Plunger Holder - Lower | 1 |
| Plunger Holder - Upper | 1 |


# CAD Model
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH35dfcQT936092f0e430b83a7ea45015764?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>



* [Arduino Code](https://online.flippingbook.com/view/300185945/)

{% include gallery caption="Arduino Setup" %}
