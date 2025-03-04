---
title: "Syringe Pump"
excerpt: "This syringe pump deleivers precise amounts of fluid at the push of a button!"
header:
  image: /assets/img/LEDscreen.jpg
  teaser: /assets/img/syringepump.jpg
gallery:
  - image_path: assets/img/code.png
   
---

## Introduction
Syringe pumps are motor driven devices used to administer fluid over a period of time. They are used for various purposes, most notably in clinical settings and medical facilities for administering medicines and other drugs, and also in research settings, particularly for microfluidic, biomedical, and chemical applications. For medical applications in particular, syringe pumps are often used to deliver intravenous (IV) therapeutics over several minutes at a constant rate, reducing the risk of human error and freeing up time for medical personnel. Syringe pumps are also used to deliver painkillers and other medications, ensuring medication levels within patients are always at an ideal level. Several aspects of a syringe pump make them beneficial for medical and research applications, including the fact that they are sterile and can limit cross-contamination when switching between syringes, they allow fluids of high viscosity to be pumped, and they are highly accurate. The mechanism behind syringe pumps is powered by a motor turning a lead screw. A nut on the lead screw is coupled to the plunger on the syringe with a plunger holder. As the motor and lead screw turn and the nut is driven down the length of the screw, the plunger is pushed forward, releasing the liquid contained in the syringe. While this is a relatively simple mechanism that requires few components and simple digital logic systems, syringe pumps that are commercially available can cost several hundred dollars. 


## Design
The design and build of the syringe pump was constrained by a few key design requirements. First, the pump had to be able to function properly for syringes of two different sizes (20 mL and 5 mL capacity) without having to use fasteners to switch between the syringes. Second, the pump had to be driven by a stepper motor coupled to a lead screw. Third, the flow rate of the pump, given in mL/min, had to be able to be easily controlled in the Arduino software. Fianlly, the motion of the syringe had to be triggered by a button and a limit switch had to be triggered when the plunger reached its limit. 


# First Design Constraint: Compatible for Two Different Syringe Diameters
In order to be compatible with two syringes of different diameters, this syringe pump is based off a two-layer design. Each layer has three main components: a plunger holder, a back barrel stabilizer, and a front barrel stabilizer. The plunger holder secures the back plunger of each syringe by allowing it to slot into the holder, supporting it for both forward and backward actuation. The back barrel stabilizer allows the back barrel of each syringe to slot into the holder in a similar fashion, holding the back barrel of the syringe in place so that the plunger is able to move forwards and backwards. The front barrel stabilizer holds the tip of the syringe in place, providing further stability to the syringe as the plunger moves. The bottom layer of components are designed to work with the larger diameter syringe. To adapt the device to accommodate the second smaller diameter syringe, the upper layer components are able to slot into the bottom layer components. The smaller syringe is then able to slot into the top layer parts and operate the same way as the larger syringe. To protect the electronics from finger and water intrusion, a box was designed around the entire electronics system with a lid. The lid contains two holes to run wires from the limit switch and motor into the electronic components, but those holes are behind where the syringe extrudes, so there is little risk of water intrusion.

# Second Design Constraint: Stepper Motor Operation
A 2 mm pitch lead screw and 8mm diameter linear rod pass through the plunger holder, back barrel stabilizer, and front barrel stabilizer on the bottom layer. A linear bearing press fit into the plunger holder traverses the linear rod, ensuring that the three components stay aligned on the same axis. The lead screw is driven by a Nema 17 stepper motor, connected by a flexible coupler to adjust for variances in axial alignment. A motor mount holds the motor in place and is mounted to the aluminum extrusion along with the other components on the first layer. As the motor turns, the lead screw rotates with it, and the lead screw nut mounted to the plunger holder converts this rotation into linear motion, moving the plunger. In order to achieve clockwise motion of the stepper motor, the direction pin has to be pulled to high. This was controlled through the connection to Arduino pin 5. To achieve finer resolution and reduce the amount of noise generated by the motor, quarter-step microstepping was used. Based on the AccelStepper library documentation, the maximum step rate that the Arduino can handle is 4000 steps/sec. The maximum theoretical flow rate for the large syringe is 163 mL/min and 64.5 mL/min for the small syringe. These values are clearly too high to be used in reality but based on the capabilities of the motor and the microcontroller, in theory these flow rates would be able to be met. The smallest volume of fluid that can be dispensed is 1 mL for the large syringe and 0.4 mL for the small syringe. This is based on how close the plunger holder is able to get to the barrel back stabilizer before the limit switch is triggered, stopping flow. 

# Third Design Constraint: Flow Rate Controlled by Arduino
The Arduino was programmed using an Arduino Mega microcontroller. The AccelStepper library was imported for the Nema 17 stepper motor and the LiquidCrystal library was used for the LCD. All components of the syringe pump were first instantiated - the motor, buttons, LEDs, potentiometer, and LCD. Pin numbers were assigned to all the various buttons, LEDs, and potentiometer. Calculations for controlling the step rate of the motor in steps/second based on the desired input flow rate in mL/min were then programmed in for both the large and small syringes. In the “Setup” function, each of the LEDs and buttons were set to either input (buttons) or output (LEDs), with all the input modes being set to pull up. The text displayed initially on the LCD was also started. In the “Loop” function, a series of conditional statements were used to control the operation of the syringe pump. A set of Boolean variables were used to keep track of the run status of the pump, recording whether it was a new process (the pump has completed a full range of motion to the limit switch and is ready to restart) and whether or not each of the start, forward, and reverse buttons have been pressed for the first time. This is important to keep track of to ensure that the flow rate is only being updated from the potentiometer at certain times for new process so that it isn’t updating during every cycle of the “Loop” function. The analog values from the potentiometer are read in the “Loop”, ranging from 0 to 1023, and those are mapped to a range of flowrates from 0 to 10 that correspond with the turning of the dial. Additionally, each condition of the syringe has a corresponding RGB LED color that is set.


# Foruth Design Constraint: Usage of Buttons & Limit Switch
There are three buttons mounted on the front of the box: Start, Forward, and Reverse. The syringe pump pushes at the designated flowrate when the start button is pressed. The forward and reverse buttons are used to calibrate the position of the plunger holder for loading the syringe such that the user does not need to manually turn the lead screw. The flow rate can be adjusted by turning the potentiometer dial mounted on the box lid. An RGB LED is also mounted on the box and displays green when the pump is active, yellow when paused, red when the limit switch is triggered, purple when moving in reverse, and blue when moving forward. The limit switch is triggered when the plunger holder pushes the plunger all the way to the back barrel stabilizer, indicating that the syringe is fully empty. The lid has holes for mounting the potentiometer and running wires from the limit switch and stepper motor into the circuitry housed in the box.

## Pump Operation
To operate this device, the user should use the 3 buttons and the potentiometer dial. The black Start button starts and stops the syringe pump. When the button is down, the syringe is gradually emptied. When it is pressed again, the movement is paused, then resumed with another press of the button. The blue Forward button moves the syringe forward while pressed and the red Reverse button moves backwards to adjust the start position. The potentiometer dial adjusts the flow rate, which is displayed on the monitor, along with the time remaining before the liquid is empty. The flow rate can only be set in between cycles after the limit switch resets; if the pump is paused before emptying the syringe completely the limit switch must be manually triggered to adjust the flow rate. The status of the syringe pump can be observed through the color of the LED: cyan indicates the flow rate is ready to be set, green indicates the machine is running, yellow indicates it is paused, blue indicates it is moving forward, purple indicates it is moving backwards, and red indicates it is out of liquid. 


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


## CAD Model
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH35dfcQT936092f0e430b83a7ea45015764?mode=embed" width="640" height="480" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>


{% include gallery caption="**Arduino Setup**" %}

