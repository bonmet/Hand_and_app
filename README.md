# Hand_and_app
Hand control by app, and codesys PLC, user can connect with pc, and  android cell phone. user can drive the hand by command or by voice control, we are support Google API, and Baidu API. For someone who can not used google.

HAND Technical Specification
Release: 1st June 2016


 







	Scramp Robotics GmbH
 
1.	Overview

The UB-hand (UBH) is an anthropomorphic robotic hand that mimics faithfully human prehensile and manipulation capability thanks to the high number of controlled degrees of freedom and similarity of the hand kinematics of an adult man.

The UBH has been designed as a flexible and versatile end-effector for industrial robots and it is able to handle a large set of tools and objects originally conceived for human operators.  

The UBH is provided with five fingers and a wrist. Each finger is composed of five links and four rotational joints, three of which are independently controllable. The upper fingers, namely index, middle, ring and pink share the same design and kinematics apart from the dimensions of the links that differ in order to increase anthropomorphism and dexterity. The thumb has samenumber of DOFs but different kinematic to improve the opposability with the upper fingers. The wrist has two orthogonal rotational joints that can be controlled independently. In total the UBH has seventeen actuated DOFs.
Synthetic tendons pulled by servomotors located in the forearm realize the actuation. Every finger needs five motors to control independently its DOFs, while the wrist needs four motors to actuate the two DOFs. In total the UBH is equipped with twenty-nine servomotors. The routing of the tendons within the fingers is endoskeletal, which means that internal cavities of the phalanges are used to be guide the tendons from their anchoring points on the finger to the pulleys flanged on the motors shafts. In order to simplify the routing of the tendons through the wrist elastic conduits have been used.

The design is modular, therefore any variation of the original version is possible on request, including changes in dimension, number of fingers, DOFs independently controllable, presence of the wrist, maximum force at the finger tips, tactile sensors, right or left hand.

The fingers are manufactured using 3D printing in ABS, which allows obtainingappropriate mechanical performance, complex geometries and low production costs.

The UBH can be considered as a fully integrated system since the actuation, sensing and control system are embedded in the hand and in the forearm. It offers both wired and wireless interfaces to communicate with external devices.

In the following sections more detailed information about the kinematics, the actuation, the sensors and the control of the hand will be given.
 
2.	Mechanical Details

The UBH has been designed to have similar shape and size to a typical right adult male hand. In Fig.1 the frontal and lateral profile of the device is shown.
The robotic hand can be divided in three main sub-assemblies:
	The hand composed of five fingers and the palm;
	The wrist composed of the link with palm, an intermediate articulation and the link with the forearm;
	The forearm in which all the servomotors are located.

 
Figure 1 Mechanical design of the UBH and maximum encumbrance dimensions
The entire volume occupied by the device can be confined in a bounding box of  [606.46, 205.1, 111.2] mm, while the hand has a maximum encumbrance of [221.01, 205.01, 56.14] mm.

The fingers are composed of five links:
	Metacarpal bone;
	Proximal-Metacarpal articulation;
	Proximal phalange;
	Middle phalange;
	Distal phalange.

Revolute joints connect the links:
	Metacarpophalangeal joints (orthogonal)- (2 DOFs);
	Proximointerphalangeal joint (1 DOF)
	Distalinterphalangeal joint (1 DOF);

The dimensions of the fingers phalanges are summarized in Table 1. 
 
Figure 3 Mechanical design of the thumb
 
Figure 4 Different dimensions and design of the fingers

	THUMB	INDEX	MIDDLE	RING	LITTLE
PROX-MC ARTICULATION	18	12	12	12	12
PROXIMAL PHALANGE	25	37	44	39	34
MIDDLE PHALANGE	30	25	25	25	25
DISTAL PHALANGE	34	27	27	27	27
Table 1 Dimensions of the phalanges
a)	Weight
The hand and forearm have a total weight of 4.5 Kg.
b)	Speed 
Movement speed can be set by the control. The maximum speed achievable for the complete closure of the fingers is about 0.3 s.
3.	Actuation System

The actuation is based on electric servomotors. On the output shaft of the motors is flanged a pulley where an extremity of the tendon is anchored. The tendon is guided through the forearm and the wrist by an elastic conduit. The other extremity of the tendon is anchored directly on the phalange.
The servomotors are produced by Robotis  INC and the model adopted is DynamixelRX-28. In Figure 5 the Dynamixel RX-28 is shown, while in Table 2 the main technical parameters are reported.
The UBH integrate 29 RX-28 to fully actuate the fingers and the wrist.

 
Figure 5 The servomotorDynamixel RX-28
WEIGHT	72g
DIMENSION	35.6mm x 50.6mm x 35.5mm
RESOLUTION	0.29°
GEAR REDUCTION RATIO	193 : 1
STALL TORQUE	3.7N.m (at 18.5V, 1.9A)
NO LOAD SPEED	85rpm (at 18.5V)
RUNNING DEGREE	 0° ~ 300° orEndless Turn
RUNNING TEMPERATURE	-5℃ ~ +80℃
VOLTAGE	12V~18.5V (Recommended Voltage 14.8V)
COMMAND SIGNAL	 Digital Packet
PROTOCOL TYPE	RS485 Asynchronous Serial Communication (8bit,1stop, No Parity)
LINK(PHYSICAL)	 RS485 MultiDropBus
ID	 254 ID (0~253)
COMMUNICATION SPEED	7343bps ~ 1 Mbps
FEEDBACK	Position, Temperature, Load, Input Voltage
MATERIAL	Full Metal Gear, Engineering Plastic Body
STANDBY CURRENT	50 mA
Table 2 Technical specification of the servomotor Dynamixel RX-28
The pulleys on the motor side have radius 11.5 mm.
In Table 3 the pairing between motors and tendons of the fingers and wrist is shown. The label “sign” indicates the mounting direction of the motor, and therefore the direction in which the motor pulls the tendon.

Table3Pairingbetweenmotors and tendons
The tendons are routed along circular paths obtained directly on the body of the phalanges and of the wrist. In Table 4 for each joint of the fingers are reported the radii and the maximum travel. The DIP joint is mechanically coupled with the PIP joint with a ratio of 0.7.

 
Table 4 Fingers and wrist joints data
4.	Control and Communication

The control of the hand can run either in an external PC or in a dedicated processor integrated with the hand. The inputs of the controller are the seventeen joint references of the fingers and the wrist. The control software translates the hand joint references in motors references. 
The user can additionally set:
•	the speed of execution of the movement;
•	the maximum torque of the motors;
•	the PID constants of the position motor controller.

The hand joint references can be generated locally by means of a user interface or can be sent from a remote machine through a UDP connection.  
