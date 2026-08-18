# Industrial-tank-level-control
PLC Project built and simulated entirely on CODESYS showcasing a program that automatically controls the level of liquid inside of a tank with overfill sensors, fault detection and warnings. It is programmed using the Functional Block Diagram (FBD) language.  I've also designed a visualization to go along with it acting as the HMI.
A simulated tank level POU is implemented into the main tree of the FBD network as a separate ST block to simulate the tank level filling process in order to demonstrate the logic behind the pump system.
The logic implements an alarm latching block that is only cleared when the fault reset button is iniatited, preventing "alarm fatigue" and the need for an operator to physically clear the fault.
The video demonstration can be viewed here https://youtu.be/_G4MfmdS9TY
