# Dumping the ESP32 Firmware on a Yoto Mini v2 (2023)

1.  Follow the [Battery Replacement guide](https://us.yotoplay.com/mini-battery-replacement-kit-how-to-guide) from Yoto (steps 1-8)
2.  Pop off the two control knobs and remove the two 10mm nuts  
![dtefoaym2_01.jpg](/img/dtefoaym2_01.jpg)
3.  Remove the 3 screws holding the board to the case  
![dtefoaym2.jpg](/img/dtefoaym2_02.jpg)
4.  Optional - After removing, flip the board and remove the headphone port cover (2 screws) 
![dtefoaym2_03.jpg](/img/dtefoaym2_03.jpg)

5.  Solder a 2mm header/connector (e.g. JST) to the pins and connect them to your serial device as follows  
![dtefoaym2_04.jpg](/img/dtefoaym2_04.jpg)
![dtefoaym2_05.jpg](/img/dtefoaym2_05.jpg) 

If using a raspberry pi, the following mapping should be used

| Header R->L | ESP32 - Pin | ESP32 - Label | Rasp Pi - Pin | Rasp Pi - Label | 
| - | - | - | - | - |
| Pin 1 | Any GND (1, 38, etc) | GND | Any GND (6, 9, etc) | GND | 
| N/A | 2 | 3V3 | 1 | 3V3 |
| Pin 4 | 3 | EN | 1 via 10k resistor | 3V3 + 10k ohm |
| Pin 5 | 25 | IO0 (zero) | GND via button | na | 
| Pin 2 | 34 | RXD0 | 8 | TXD0 |
| Pin 3 | 35 | TXD0 | 10 | RXD0 | 

- Enable UART (just hardware, not console)
- Install ESPTool
- Run ‘esptool.py -p /dev/ttyS0 read_flash 0 ALL yoto_mini_v2.bin’
- When “Failed to get PID…” appears do the following
	- Press and hold Boot/Flash button
	- Press and release Reset button
	- Release Boot/Flash
- Flash should start dumping (takes 10-15 mins)

6. Once you have the bin file, clone/install [esp32_image_parser](https://github.com/tenable/esp32_image_parser)

7.  Apply the following fixes (or use my forked version - aaronr8684/esp32_image_parser/tree/fixes_3_13_15)
	- [https://github.com/tenable/esp32_image_parser/pull/3/files](https://github.com/tenable/esp32_image_parser/pull/3/files)
	- [https://github.com/tenable/esp32_image_parser/pull/10/files](https://github.com/tenable/esp32_image_parser/pull/10/files)
	- [https://github.com/tenable/esp32_image_parser/pull/13/files](https://github.com/tenable/esp32_image_parser/pull/13/files)
	- [https://github.com/tenable/esp32_image_parser/pull/15/files](https://github.com/tenable/esp32_image_parser/pull/15/files)

8.  Grab the partition table via 
```
python esp32_image_parser.py show_partitions ../../yoto_mini_v2.bin
```
9.  Get the ELF files via
```
python esp32_image_parser.py create_elf ../../yoto_mini_v2.bin -partition ota_0 -output yoto_ota_0.elf
```
11.  Run again for ota_1
12.  Use a decompiler to read the ELF files (like Ghidra or IDA Pro)