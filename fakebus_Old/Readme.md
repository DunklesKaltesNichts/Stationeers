It basically works like a shared bus, except that the "bus" here is a logic memory.  
It is currently written by some bus masters and read by any number of ICs.

This is certainly completely overkill and overcomplicated.  

there is no return channel.

Protocol:

XXYYZZZ  

XX: Address of IC10  
YY: Command  
ZZZ: Value  

Address:
99: Broadcast

Command: 

anything less than 40 is interpreted as a bitmask. the value is ignored. for easy switching on and off of things.  
Since I use a maximum of 5 pins in addition to the pin for the memory, 31 should be the end.  
Bitmask: 1, 2, 4, 8, 16

40-49: not used. Maybe this will become a query response protocol later on. like I²C.  
41: ask something.  
42: response  


50-59: Room Pressure Controller  
51: Set the desired room pressure.  
52: Flow. actually, only a difference in the active vents in the Pressure external.  
(53: Evacuate. But can also be done with 51000 and 52000)

4052050:  
set the Flow in my greenhouse to 50. this sets the blowing in vent to 125 and the blowing out vent to 75.    

80-85: Set the housing setting at the corresponding pin.  
89: set all Pins  
xx84102 > set the Housing setting at pin 4 (D3) to 102  
For my light control to select the flow.  
100: all off  
101: running light  
102: filling light  
103: all on  
112: Some lights flash, while others are permanently lit.

9989112:   
Broadcast 
set all housings to 112  
Storm in 60 seconds, close the garage doors, activate lights and sirens, call AMIEe back or send them to safety.


90-99: reserved for alerts and warnings
  
6591412:  
send to control room IC.  
the chip in the control room then sets an LED display to the error code and switches on a Klaxon speaker and flashing light if required.

411: Pressure in assigned tank low.  
412: Overpressure alarm in the assigned tank. For information only. The overpressure valve runs autonom.  
401: Oxygen Filter full.  

some of my ICs have a logic memory as error memory. a controller reads this and sends a message to the "bus" if necessary. 
then you run to the appropriate chip, check the error memory, turn off the alarm and fix the error. like an engine control light in a car. ;)

