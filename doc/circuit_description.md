## Clock source
LTC6900 is used to generate a 10MHz clock signal for the DDS chips.  The clock speed is set by the resitor.
![CLOCK](https://github.com/EIT-team/Mini_CS_Altium/blob/master/doc/images/clock.PNG)

## Negate voltage generator
The op amps used in the Howland Current Pump require a negative voltage. The LTC1044 generates this.
![VOLTAGE](https://github.com/EIT-team/Mini_CS_Altium/blob/master/doc/images/Volt_converter.PNG)

## DDS and analog filter
AD9833 generates a 10-bit sine wave with 0.6V amplitude, the frequency is programmed over SPI from the Arduino. The two op-amps impement an image filter to reduce the higher frequency components on the sharp edges of the DDS signal.
![DDS](https://github.com/EIT-team/Mini_CS_Altium/blob/master/doc/images/DDS.PNG)

## Howland Current Pump
An improved HCP converts the DDS output voltage into an output current. 4 output resistors are included to allow for selection of the output current, using the header connection P1. For testing/debugging, the two HCP outputs are also routed to header P2, before they go to the switch network.
![HCP](https://github.com/EIT-team/Mini_CS_Altium/blob/master/doc/images/HCP.PNG)

## ADG731 Switches
Two ADG731 32-way switches route the HCP outputs (Iout+ and GND) to the output connector pins. Note that there isn't a direct map from switch number to output pin, due to PCB routing constraints.
![SWITCHES](https://github.com/EIT-team/Mini_CS_Altium/blob/master/doc/images/switches.PNG)

## Output Connectors
The 32 outputs from both switches are routed to first 32 pins of the omnetics conenctor. 4 pins (19-22) are routed to generic output pins, to allow the switches to be tested without needing to use the Omnetics.
![CONNECTORS](https://github.com/EIT-team/Mini_CS_Altium/blob/master/doc/images/connectors.PNG)

## Input Header
The bank of input headers, P5, is used to provide power (VDD, GND) and SPI control signals to the board. The DDS chips and switches share SPI data and clock signals, but each have a separate FSYNC line. The LED indicates if VDD is being provided.
![HEADER](https://github.com/EIT-team/Mini_CS_Altium/blob/master/doc/images/header.PNG)
