# Solar Movement Tracker

This is a Single axis solar tracking system. In this system, the whole solar panel moves from east to west in a day to point in the direction of the sun. Use of a solar tracker circuit in the field of energy production will increase its efficiency. This system can also be successfully implemented in other solar energy based projects like water heaters and steam turbines.

This solar tracking system comprises of a solar panel, Arduino microcontroller and sensors. For this system to operate there must be emission of light through the sun. The LDRs serve as the sensors to detect the intensity of light entering the solar panels. The LDR then sends information to the Arduino microcontroller. The servo motor circuit is then constructed. The servo has 3 pins of which the positive side is connected to the +5v of the arduino microcontroller. The negative of the servo is connected to the ground. The data point on the servo is connected to the analog point on the microcontroller. A potentiometer is connected so as to regulate the speed of the servo motor. 

![](iamges/Circuit_Diagram.jpg)

