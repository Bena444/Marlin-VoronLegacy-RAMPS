

<div align="center">
  <h1>Marlin for Voron Legacy and RAMPS 1.4</h1>
  
  Additional documentation can be found at the [Marlin Home Page](//marlinfw.org/).
</div>

## Independent Z Motors

As you may know, the [Voron Legacy](//github.com/VoronDesign/Voron-Legacy) uses two motors on the Z axis, which leads to the necessity of tilt calibration. Usual RAMPS 1.4 builds use a single stepper driver for both Z motors. 

I've modified the pins.h header to turn the unused E1 driver into the second Z motor driver. It fully redefines the second E motor as the second Z motor (Z2), simplifying other modifications in the firmware.

The command for tilt adjustment is G34, Marlin calls it  Z Steppers Auto-Alignment. I put it before G29 in my start G-code.

## Klicky

This fork is also set up for the [klicky probe](//github.com/jlas1/Klicky-Probe). 

The exact position for the probe and probing routine can be found in the respective config.h section.

## Extruder
The specific e-step values are made for a generic dual gear extruder with a 4:1 gear ratio.

## Display
I used a generic RepRapDiscount Smart Controller display on my build.

## Input Shaping
I've tested this feature but chose to keep it deactivated. It renders the interface useless during printing.

## Thermistors
I also changed the analog pin associated with the thermistors due to an accident with my original Arduino.

  Pin|Thermistor
  ----|----
  15|TEMP_0
  13|TEMP_1
  14|BED_PIN

Essentially, this means that you will have to plug your hotend thermistor into the A13 pin instead of the usual A15. If you get it wrong, your temperature will be either negative or at its maximum, so pay attention to the UI.

## Disclaimer
This fork is provided as is. I do not take responsibility for any ill use of this modification of the Marlin firmware. I have not modified any safety measures, but still changed a setting related to temperature measurement. Do not leave your printer running unattended. This was made specifically for my use case, but I'm publishing it because it may help out someone else.

## License

Marlin is published under the [GPL license](/LICENSE) because we believe in open development. The GPL comes with both rights and obligations. Whether you use Marlin firmware as the driver for your open or closed-source product, you must keep Marlin open, and you must provide your compatible Marlin source code to end users upon request. The most straightforward way to comply with the Marlin license is to make a fork of Marlin on GitHub, perform your modifications, and direct users to your modified fork.
