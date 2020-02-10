# Packaging-system-in-Rockwell-Studio-5000
Chocolate packaging control with Allen Bradley PLC

Project Description

Two kind of chocolate boxes are carried in a conveyor belt to be filled with chocolate in a filling station. There is a proximity switch which closes when a box arrives near it to be filled. The box to be filled with Reeses is Red labeled and the box for Harshey is blue labeled. A photo eye sensor is used to detect the color of the label. When a Red label box arrives, the Reeses hopper starts to fill the box and when a blue label box arrives, the Harshey hopper starts to fill the box. A level sensor is used to detect if the box is full. When a box is full, it will be sent out from the filling station and the next box will come to the filling station automatically.

How I built it

I divided the whole process into four stages. 
Bring box: The proximity switch is open that means there is no box near it. Both blue and red light sensors are off so the level sensor is off. In this condition the box will be brought to the filling station.
Fill Box: When a box is at filling station, the proximity switch is closed. Either red light switch or blue light switch is closed depending on the label of the box and the level switch is open to fill the box with chocolate.
Unload: To unload the box from filling station all conditions are same as fill box mode. But the level switch is closed indicating the box is full.
Intermediate: When a box arrives in the filling station, it is needed to be stopped before label detector sensor starts working. Intermediate stage is created for this reason. It is in between stage of bring box and fill box mode. It is also used to prevent the mixtures of two different kinds of chocolates.
Conveyor motor is kept running in bring box and unload modes. Harheys hopper trigger is energized when it is fill box mode and blue light switch is closed. Harsheys hopper bit is energized by the Harsheys trigger and it is latched to stay energized if it is in fill box mode while the level switch is open. Reeses hopper is also controlled similarly.

How I tested it

I ran the program on Emulator. The conveyor motor started immediately but both hoppers were off. Then I forced only the proximity switch on. The conveyor motor became shut off, and both hoppers were remain de-energized. After that I left the proximity switch closed and forced the red light switch on. The conveyor motor and the Harsheys hopper remained off, but the Reeses hopper was energized. At this stage the proximity switch is closed and I forced the red light switch off and the blue light switch on. The conveyor motor remained off, but the Reeses hopper was de-energized and the Harsheys hopper was energized. In next step, the level sensor is forced on. Both hoppers became de-energized and the conveyor started back up to move the box forward. Finally, I forced the proximity switch, the level sensor and both red and blue switch off. Both hoppers remained de-energized and the conveyor kept running.
