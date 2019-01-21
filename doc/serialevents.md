The WavDJ VM-108 communicates to the PC via an internal DS14C232 TTL - RS232 converter


# Serial Data Format
 - Baud: 38400 
 - Parity: Even 
 - Data Bits: 8 
 - Flow: RTS/CTS


# Key Event Format

The VM-108 sends key events via serial in the format of:
{ClusterId} {ButtonId} {End of Command Bytes} 

End of command bytes: 0x8C 0x04

- Example: Animals FX button = 0x83 0x00 0x8C 0x04

## Button Types
- **Keyboard** - unique in that they have two cluster IDs for the pressed (which repeats) and released state
- **Momentary** - send a single event on press, this does not repeat and does not fire an event on button release
- **Sliders** - internally these are potentiometers, the value is send as the ButtonID when it is changed
- **Slider Toggle Buttons** - send entire group state as binary
- **Switches** - sends switch state on change (4 times, bouncy?)

## Keyboard
*Keyboard is numbered C - E, then C# through D#*

*Key press repeats as long as key is pressed*

|Group Name|Cluster ID|Button Values|
|--|--|--|
|Key Press|0x80|0x00 - 0x10|
|Key Release|0x81|0x00 - 0x10|

## Momentary Button Clusters
|Group Name|Cluster ID|Button Values|
|--|--|--|
|WAV Effects|0x83|0x00 - 0x1D|
|Keyboard Instrument|0x84|0x00 - 0x11|
|Playback Control|0x85|0x00 - 0x05|
|Music Style|0x86|0x00 - 0x0B|
|Rhythm|0x87|0x00 - 0x05|
|Block|0x88|0x00 - 0x05|
|Mouse|0x89|0x00 - 0x07 - Directions<br/> Clockwise, starting up, include diagonal <br/> 0x08 - Left click  <br/> 0x09 - Right Click
|Drums|0x8A|0x00 - 0x05|
|Tempo|0x8B|0x00 (up) <br/> 0x01 (down)


## Sliders
*Pot values roughly 0x00 - 0x7F*

|Group Name|Cluster ID|
|--|--|
|Mic|0x8D|
|FX|0x8E|
|Key|0x8F|
|CD-ROM|0x90|
|Line In|0x91|
|Seq|0x92|
|Effects Wheel|0x94|


## Slider Toggle Buttons

|Group Name|Cluster ID|
|--|--|
|Slider Toggle Buttons|0x96|

Buttons send the state of buttons in binary where button state maps to 1/0 of the right most bits in the hex value.

Example: All on except Line In and Seq: 

    0x3C = 0 0 1 1 1 1 0 0 (2 left most bits not used)

## Switches
*Note: These seem bouncy and send command 4 times on change*

|Group Name|Cluster ID|Button IDs
|--|--|--|
|Scratch / Pitch Bend|0x97|0x00 - Pitch Bend <br/> 0x01 - Scratch|
|Octave|0x97|0x00 - 0x07
