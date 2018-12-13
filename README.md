# Self-calibrating-surgical-bed


Surgical bed that can track a point on the subject placed on the operating table and move accordingly.

## Motors


The basic mechanics for the XY motors came from a kit
(http://learn.makeblock.com/en/xy-plotter-robot-kit/)  We used The mechanics from
here meaning the two motors and the one motor driver.  The control was supplied by
the rasberry Pi.  

The motors used were Nema 17 bipolar stepper motors with four leads.  They were very
powerful and when they were held in position could draw 1.7 Amps and were very hard
to move. These four wires controlled two sets of coils, both phase A and phase B.

The controllers for the motors both used the stepper motor driver A4988 (included
here) 

The schematic that we used was the A4988 driver module (A4988 Stepper Motor Driver
Module, Red PCB with Heat Sink for CNC 3D Printer RepRap StepSticknd) and was wired as follows:
![](circuitDiagram.PNG)




