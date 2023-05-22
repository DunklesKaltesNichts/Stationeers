New attempt of a bus.

this is a master - servants bus system.
many masters ask for things and the servants answer.
This time with bitwise operations.

Limits:

current 254 Transmitter and Receiver per bus.



### Packet Format
`AACCRRDDDD`

`AA`: 8 bits, target address, $00 and $FF (255) are reserved  
`CC`: 8 bits, command, $00 and $FF are reserved  
`RR`: 8 bits, status code, $00 are reserved  
`DDDD`: 16 Bits, Values


### Address:
$00 must not be used  
$FF is reserved for broadcast, current for alarms

### Command:
the different commands. they should be defined at the target.

### Status Code:
similar to HTTP status codes

$00 or $FF should be set at the command.

Response: 

100: OK, command understood, possible answer in the process

200: CMD Fail, command not available  
201: CMD Fail, command available, values not available  
202: CMD Fail, command available, timeout subsequent system  

### Values:
the responses to the appropriate command, if applicable.
