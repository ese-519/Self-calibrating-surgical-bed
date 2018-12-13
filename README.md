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

Starting from the top right and working down we see the following pins:

* VMOT – The motor DC supply voltage (positive). The maximum voltage is 35 volts.
* GND  (Motor) – The motor supply voltage ground.  This was connected straight to the negative
	voltage supply.
* 2B, 2A – The connections to coil 2 of the bipolar stepper motor.
* 1A, 1B – The connections to coil 1 of the bipolar stepper motor.
* VDD – The logic supply DC voltage. This was connected to a separate power supply that
	supplied 5V to the drivers reference circuit.
* GND – The logic supply ground. 


Now looking down the other side of the A4988 module:

* ENABLE Bar – This is an active low connection, when brought low (ground) the A4988
	module is enabled. To get the motors to work, this needs to be held low.
	Turning this high leads to a rapid shut off and should be used for safety.
* MS1, MS2, MS3 – These three connections determine the microstepping mode of the A4988 module. By setting the logic levels here you can set the motor to Full, Half, Quarter, Eighth, Sixteenth steps.
	We set these to Quarter by setting them to (low, high, low).  
* RESET Bar – This is an active low line that will reset the module. This must be
	 pulled high. it is pulled high.
SLEEP – If this line is set low the module will enter a low-powered sleep mode and consume minimal current. By tying this line to the Reset pin the module will always be on at full power consumption.
STEP – This is how you drive the motor from an external microcontroller or square wave oscillator. Each pulse sent here steps the motor by whatever number of steps or microsteps that has been set by MS1, MS2 and MS3 settings. The faster you pulse this the faster the motor will travel.
DIR – The direction control A high input here drives the motor clockwise, a low will drive it counterclockwise.


