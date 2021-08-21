Protocol

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

50-59: Room Pressure Controller  
51: Set the desired room pressure.  

52: Flow. actually, only a difference in the active vents in the Pressure external.  

60-65: Set the housing setting at the corresponding pin.  
69: set all Pins  
64102 > set the Housing setting at pin 4 (D3) to 102  
For my light control to select the flow. (100: Off, 101: running light, 102: filling light, 103: all on)  

Examples  
9969112: Broadcast, set all housings to 112 > Storm, close the garage doors, activate lights and sirens.  
4052050: set the Flow in my greenhouse to 50. this sets the blowing in vent to 125 and the blowing out vent to 75.  
