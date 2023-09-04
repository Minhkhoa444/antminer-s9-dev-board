# antminer-s9-fpga-private
The Antminer S9 control board can be used as a development board the same as the famous EBAZ4205 board.
As with the EBAZ4205 board, this Antminer S9 control board also contains a powerful Zynq 7000 SoC (xc7z010clg400-1) and some identical IO capability like the EBAZ4205. However, there are several differences between the 2 board:
* The EBAZ4205 only has 10/100Mbps Ethernet transceiver (WIZnet IP101GA), the Antminer S9 has 10/100/1000Mbps Ethernet transceiver (Broadcom B50612).
* The EBAZ4025 only has 256MB of DDR3 RAM, the Antminer S9 has 512MB of DDR3 RAM in total.
* To switch the boot mode on the EBAZ4205, you must desolder/solder some resistors, on the Antminer S9 you just need to switch jumpers.
* The EBAZ4205 has more PL IO pins available compared the Antminer S9 control board.
* The EBAZ4205 has dedicated crystal for both PL and PS, the Antminer S9 only has crystal for PS, PL clock must be derived from PS.
* The EBAZ4205 UART is already connect to the PS, on the Antminer S9 it is connected to an unsoldered level shifter IC (Texas Instruments LSF0102DCTR).

You can follow the tutorial from Digilent on how to install board files [here](https://digilent.com/reference/programmable-logic/guides/installing-vivado-and-vitis).

## Boot mode
|         | JP0 | JP1 | JP2 | JP3 |
|---------|-----|-----|-----|-----|
|   JTAG  |  0  |  0  |  0  |  0  |
| microSD |  0  |  1  |  0  |  1  |
|  QSPI   |  0  |  0  |  0  |  1  |
|   NOR   |  0  |  0  |  1  |  0  |
|  NAND   |  0  |  1  |  0  |  0  |

## Note about PS
* Since the level shifter IC U7 is not soldered, the preset file will use UART0 since MIO34 and MIO35 pins are already available on J7 and J8 respectively.
* Since PL crystals Y3 and Y4 are not soldered in, the preset file will derive PL clock from PS clock.
