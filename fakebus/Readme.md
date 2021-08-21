It basically works like a shared bus, except that the "bus" here is a logic memory.  It is currently written by a single bus master and read by any number of ICs.

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


60-65: Set the housing setting at the corresponding pin.  
69: set all Pins  
64102 > set the Housing setting at pin 4 (D3) to 102  
For my light control to select the flow.  
100: all off  
101: running light  
102: filling light  
103: all on  
112: Some lights flash, while others are permanently lit.

Examples:

9969112:   
Broadcast 
set all housings to 112  
Storm in 60 seconds, close the garage doors, activate lights and sirens, call AMIEe back or send them to safety.

4052050:  
set the Flow in my greenhouse to 50. this sets the blowing in vent to 125 and the blowing out vent to 75.    
  
6561102:  
Control room IC.  
101: Pressure in oxygen tank low.  
102: Overpressure alarm in the oxygen tank. For information only. The overpressure valve runs autonomously.  
103: Oxygen Filter full.  
