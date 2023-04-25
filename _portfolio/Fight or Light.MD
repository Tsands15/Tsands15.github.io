---
title: "Fight or Light"
excerpt: "This punchig bag utilizes changing colors set at certain speeds to train boxing reflexes"
header:
  image: /assets/img/logo.png
  teaser: /assets/img/pb.png
gallery:
   - image_path: assets/img/PBsetup4.PNG

---
# Project Group
* Gehrig Abbattista
* Paul Abdelmessih
* Andy Haworth
* Randy Kim
* Tre' Sands


## Introduction and Background
The sponsor for this project is the Boxing Resource Center, a local nonprofit boxing gym which helps kids and adults enhance their skill and appreciation for the art of boxing.  A critical component of this sport is reaction time and being able to properly read and respond to the opponent's movements, with moves such as a dodge, block or counterattack.  Normally it would be easy to practice these skills when training with a coach or against a sparring partner, but when a boxer is training at home or the gym is crowded this becomes difficult.  The goal is to create a dynamic reaction training device to help the boxer train these skills while practicing on their own.

To address this problem, a light based training tool was developed, specifically a modified reflex bag, a small spherical punching bag mounted to a pole with a built in spring.  This new device will have LEDs embedded into the surface to flash random colored lights at random intervals. The short burst of light will provide the boxer with an unpredictable visual cue to throw a specific boxing move corresponding to the color. These moves will be decided upon beforehand, for example red equates to jab and blue equates to hook. This will enable the boxer to practice reacting and responding to an opponent while they are training alone. It forces the boxer into a reactive mindset rather than deciding what move to do when normally punching a reflex bag.

Additionally the reflex bag shall have an accelerometer inserted underneath the surface. This sensor will be able to sense when the bag is punched by detecting a sharp impulse in movement.  This data can be used to calculate the boxer’s reaction time or speed of their punches, providing instant feedback they can use in their training. Additional training modes and games can be implemented utilizing the impact detection or overall movement of the bag. 

	
This reflex bag consists of a solid 3D printed core covered in two layers of padding. This padding has spaces cut out for LED lights and diffuser channels which wrap around the ball in an easy to read pattern. These lights can randomly flash red, blue or green at randomly determined intervals. The number of colors available and the average time between the flashes can be adjusted by the boxer to set the desired difficulty level. The bag is mounted on top of a standard reflex bag pole, which can be fixed to the ground and used. Two bent washers are able to be firmly inserted into the core so when it is attached to the top using a lock washer and bolt it will be fully constrained to the pole and unable to slide off or rotate.

## Design
The prototype design is comprised of a hard-surfaced core (3D printed PLA) covered with two layers of dense but soft PVC Foam (yoga mat), with diffuser channels for the LED strip residing between the outermost foam layer such that it is embedded into the layer, rather than sitting on top of it. In addition to being structurally sound and perfectly sliding onto the pole, 3D printing comes with more advantages. It becomes easy to implement space for sensors and other equipment. The current model has a slot beneath the surface for an accelerometer as well as a path for the wires to travel down the inside. The top also has slots for bent washers to be inserted firmly inside. 

![3D Printed Core Model](/assets/img/PBsetup3.PNG)

*3D Printed Core Model*

When these washers are tightened down at the top of the pole with a bolt and lock washer, they are able to completely constrain the bag.  It is no longer able to slide up and down the pole, or rotate around it and cause the wires to become tangled. The 3D print ensures these slots are sturdy and precise to prevent movement.

Embedding the LEDS within the outer layer of the padding has many advantages: along with the diffuser channel itself, the equal height with the outermost foam layer allows a primary protection from direct hits from the trainee’s punches. Earlier designs had the LED strip more protruded, increasing the risk of failure both by direct impact as well as the shearing of the strip from the surface. Embedding the channel and LED strip solved both of these issues.

The two-layer system provides secondary impact reduction to the hard-surfaced core. Any force distributed on the LED strip, as well as anywhere on the outermost layer, is mitigated further in the first layer before it impacts the core. Tests, as will be mentioned in the Testing and Simulation section, show that the above approach had minimal damage on the LED strip as well as the core, while providing a shore strength similar to that of a normal reflex bag.


## Build
For the overview of the build there are essentially three main parts: the reflex ball, electronics and UI box, and the accelerometer. The goal of this project is to have a punchable reflex bag that lights up on certain conditions. The reflex ball has diffuser channels embedded inside of it to run LEDs through the ball. The electronics and control box has an UI as well as ways to interface the power supply with the LEDs, so that they are controllable. There is also an embedded accelerometer inside of the reflex ball, so that punches can be detected. As it is now, the accelerometer is connected to an Arduino that sends a serial signal to LabView to detect the punches. However, in future iterations of this project the punch detection software will solely be run on Arduino, so that there can be a mode that whenever the reflex ball is punched the LEDs in the ball will change to a random color.

![Data Acquisition from Accelerometer](/assets/img/lb1.png)

*Data Acquisition from Accelerometer*

The initial part of this vi obtains a half second running window of data from the accelerometer. The data acquired is the acceleration in the x, y, and z direction ranging from 0 to 1023, as the analog to digital converter on the Arduino has 10 bits of resolution. The accelerometer data is the magnitude of the x, y, and z direction. The first half second running window runs when the reflex bag is static, and takes the mean of this window to zero the future recorded values. After the value to zero new data is found, the code enters a while loop that will iterate for the rest of the program.

![Punch Detection Logic](/assets/img/lb2.png)

*Punch Detection Logic*

The data from the accelerometer is taken in 200 ms windows. Then the maximum reading and the standard deviation of that window is obtained. For a punch to be detected, three conditions have to be met: the maximum reading must be 1.6 times larger than the standard deviation of the window, the maximum reading must be above 50, and the maximum reading must be less than 5.0 times the standard deviation. These conditions provide a band where the maximum reading can be between 1.6 to 5.0 times greater than the standard deviation, the maximum value being required to be larger than fifty makes sure punches do not get registered when there is not a lot of movement of the reflex bag. When the conditions are not met, the indicator will remain off. When the conditions are met, the indicator will remain on for the value of the maximum reading multiplied by 12. This allows the led indicator to be on longer when there is a stronger punch. This is desirable because the longer the light is on the less phantom punches can occur (phantom punch - when the indicator turns on when there is no punch, stronger punches tend to result in more phantom punches)

{% include gallery caption="**Punching Bag Set Up**" %}
