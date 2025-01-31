> [!Warning|style:callout]
> Please understand that modifying your coffee machine involves working with potentially lethal mains level voltage. Do not undertake this project if this makes you uncomfortable. Understanding & utilizing safe electrical practices is critical to your safety and safely completing this project. Only start working on your machine while it's completely disconnected from the mains power socket. By agreeing to follow the below guide, you agree that the authors cannot be deemed responsible for any of the damage you induce to your house appliances, yourself, your cat, your friend, or your gold fish. It will be entirely your fault!

>[!Note]
>BOM and 3D printed parts for PCBv3 have moved to the [Home page](README.md#bill-of-materials)

# Considerations
* PCBs are compatible with 3PLN stock wiring integration or custom wiring, though custom wiring is recommended for certain machines (see the [compatibility table](README.md#Compatibility))
* PCB v3 is suitable for most single-boiler espresso machines. PCB v2 supports more connection points for wiring and and/or multiple boiler control. 
* PCB v2 housing links *(Pick one)*
  * [Rigid Housing](https://www.printables.com/model/260901)
  * [Easy Access Housing)](https://www.printables.com/model/261267)

>

# Programming/Flashing

!> Do not flash the Blackpill with the ST-Link while powering the system over USB-C.  

Flash the Blackpill using the ST-Link (connect SWDIO, GND, SWCLK, and 3.3V* - see [Prerequisites](prereq/prerequisites.md) for details). 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/117388662/262874364-c44f2eea-6a64-4731-adb8-a0c1a16089d6.png">

Flash the Nextion with the applicable nextion-*-lcd.tft on an otherwise-empty ≤32 GB FAT32 microSD card.  

Power for flashing the Nextion may be provided through the USB-C port on the Blackpill so long as you are using a USB power adapter that will supply 4.6-5.2 VDC (don't use a battery bank or PC USB 2.0 ports for power).  

*If you wish to power the system through the 120 VAC PSU to flash the Blackpill then do **not** connect 3.3V to the ST-Link unless you're sure you do not have a knock-off/clone ST-Link.

Wait for the Nextion to show the "Update Successed! (sic)" message, turn off power, and then remove the microSD card.

# Pre-install test

Connect the thermocouple to the terminals and power on the system once again. If all is successful you should:
- see a build number during boot (good Blackpill-Nextion communication)
- see a "filling boiler" message a few seconds after boot
- see a temperature reading on the screen that changes when heat is applied to the thermocouple
- see the SSR light turn on if the temperature is below the setpoint (it will flash if temp is close to setpoint)
- see a pressure value of 0.0 bar with no deviation
- *not* see the steam temp as the target

**Continue the install by referencing the 3PLN machine-specific schematics and/or install instructions that apply to your desired build path:**
* [3PLN Stock Wiring Integration](guides-stm32/3pln-stock-wiring-integration.md) page.
* [3PLN Custom Wiring](guides-stm32/3pln-custom-wiring.md) page.