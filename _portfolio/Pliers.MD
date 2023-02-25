---
title: "Print-in-Place Pliers"
excerpt: "MultiMaterial Needle Nose Pliers for all your grabbing needs"
header:
  image: /assets/img/phonecase.PNG
  teaser: /assets/img/iPhone13Assemblyrender2.png
gallery:
  - image_path: assets/img/phonecaseiterations.PNG
   
---


## Introduction
Needle nose pliers are a type of pliers that have long, narrow, tapered jaws that come to a point. The jaws of needle nose pliers are typically smooth and straight, but they may also have teeth or serrations to help grip small objects. Needle nose pliers are commonly used for tasks that require precision and dexterity, such as bending and shaping wires or manipulating small parts. They are also useful for reaching into tight spaces that other pliers cannot reach. They may also be used in household tasks, such as removing a splinter or tightening a small screw.

## Design
These needle nose pliers were made through a print-in-place method. Print-in-place methods are functional multiple-component designs, that work immediately after removal from the print bed. No post-processing or assembly is required. These models can be created with multiple single material extruders working in tandem to design models with joints placed in certain sports to allow for maximum motion or rotation when it is needed. However, these models still may be plagued with rigid movements due to the material of the print, specifically PLA in this case. To solve this issue, a more flexible material, which in this case was TPU, is introduced to a central part of the model to allow flexibility in all parts of the model.
# First Design Constraint: Moving a 3 mm Pellet
The first and most important design constraint of the pliers was usability. This was determined by how effective the pliers were at gripping and picking up a plastic pellet with a 3 mm diameter, moving it to another location, and then releasing it. In order to accomplish this task, I first designed the gap between the plier’s jaws to be as minimal as possible to make clamping east while still having enough space to clamp a 3 mm pellet. This led to the gap is approximately 7 mm wide. Additionally, the clamping power had to be enough to pick up the pellet and move it without dropping it. This led to the creation of teeth being placed at the top of the plier's head, approximately 15 on each side. This ensures the pliers get a good grip on whatever object they need to pick up. The jaw lengths were approximately 40 mm to allow enough leverage to grab an object with as little pressing force as possible.

# Second Design Constraint: Flexible Material Component
The second design constraint was having a flexible material that functioned as a spring component that keeps the pliers in an open position whenever the pliers aren’t being utilized. This was accomplished by printing the central axis of the pliers with TPU. Thermoplastic Polyurethane or TPU is a very flexible and elastic-plastic that is smooth to the touch but strong a durable at the same time. TPU was the perfect material to keep the plies open as it was rigid enough to keep a shape while there are no forces acting upon it. When the pliers’ handles are squeezed, the TPU center elongates in the x-direction, allowing the pliers' jaws to close. When the handles are released, the TPU center goes back to its original shape and the pliers open back up, creating the opening and closing movement required of the pliers. The handle and pliers’ jaws were made of a more rigid material, Polylactic Acid or PLA. This material was chosen so the pliers themselves were durable and stiff enough to hold objects.

## Print Settings
| Print Material | TPU | PLA |
| --- | --- | --- |
| Extruder Temperature | 240 C° | 215 C° |
| Bed Temperature | 60 C° | 60 C° |
| Retraction Speed | 15 mm/s | 40 mm/s |

## CAD Model
<iframe src="https://vanderbilt643.autodesk360.com/shares/public/SH35dfcQT936092f0e438d47d79f02407236?mode=embed" width="800" height="600" allowfullscreen="true" webkitallowfullscreen="true" mozallowfullscreen="true"  frameborder="0"></iframe>


{% include gallery caption="**1st and Final Iteration (left to right)**" %}





