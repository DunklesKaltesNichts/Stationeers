Protocol

XXYYZZZ

XX: Address of IC10

YY: Command
ZZZ: Value

Adress:
99: Broadcast

Command: 

Anything less than 40 is interpreted as a bitmask. 
Since I use a maximum of 5 pins in addition to the pin for the memory, 31 should be the end.

50-59: Room Controller
51: Set the desired room pressure.
52: Flow. actually, only a difference in the active vents in the Pressure external.




Bitmask
1
2
4
8
16
