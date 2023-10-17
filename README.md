# LilyGo-T-PicoC3-RECOVERY

LILYGO® T-PicoC3 ESP32-C3 RP2040 Wireless WIFI Bluetooth Module Development Board Dual MCU 1.14 Inch ST7789V Display for Arduino
https://github.com/Xinyuan-LilyGO/T-PicoC3

How to RECOVER:

For RP4020:
Plug it in so the blue light is on and hold boot while hitting Run. If the light is green, unplug and flip over the USB-C cable and plug back in. 
The go to mac Finder and drag firmware.uf2 onto the new RPI-RP2.
And then copy tft_config.py to RPI-RP2

For ESP32C3:
https://micropython.org/download/esp32c3-usb/
Download select the "ESP32 C3 with USB"
	•	First short IO9 to GND using the wire or the paper clip, then connect the board so the green LED is lit (no need to hit the BOOT button). Leave 		the wire in!
	•	Open a command window on your computer and you will see /dev/tty.usbmodem14401
	•	Erase the flash memory with this command:
		python -u -m esptool --chip esp32c3 --port /dev/tty.usbmodem14401 erase_flash

	•	Unplug the board, short IO9 to GND and reconnect the board
	•	Now flash the firmware of the ESP32:
		python -u -m esptool --chip esp32c3 --port /dev/tty.usbmodem14401 --baud 460800 write_flash -z 0x0 /path/Documents/Arduino/T-PicoC3-main/RECOVER_T-PicoC3/esp32c3-usb-20230426-v1.20.0.bin

  Ie. $ python -u -m esptool --chip esp32c3 --port /dev/tty.usbmodem1101 --baud 460800 write_flash -z 0x0 Documents/Arduino/T-PicoC3-main/RECOVER_T-PicoC3/ESP32_GENERIC_C3-20231005-v1.21.0.bin


	•	Unplug the board, plug it again normally.


Great guide:
https://www.instructables.com/Parallelism-and-Much-More-on-the-T-Pico-C3/

T-PicoC3_tft_setup
This is for LilyGo T-Pico3: https://www.tindie.com/products/lilygo/lilygo-t-picoc3-esp32-c3-rp2040-wireless-wifi/
Need TFT_eSPI library to work: https://github.com/Bodmer/TFT_eSPI
To use:
	1.	Put this file in the library path: ...\Documents\Arduino\libraries\TFT_eSPI\User_Setups\Setup138_LilyGo_TPicoC3.h
	2.	Edit ...\Documents\Arduino\libraries\TFT_eSPI\User_Setup_Select.h 
  Comment out:
  #include <User_Setup.h> 
	3.	Add line below:
  #include <User_Setups/Setup138_LilyGo_TPicoC3.h>           // Setup file for Lilygo TPicoC3



