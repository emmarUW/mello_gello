# mello_gello
...They call me mello gello  - improved models and methods for the Gello robot teleop system

This project is heavily inspired by, and will use code derived from the original GELLO project - https://wuphilipp.github.io/gello_site/

MELLO GELLO (MG) overhauls the GELLO design and replaces hardware components 
- In place of the dynamixels used in the original GELLO, MG uses "ROLLERCAN" motors from M5 stack: https://shop.m5stack.com/products/rollercan-unit-with-bldc-motor-stm32
- The RollerCan device includes a BLDC motor and an encoder addressible via I2C or CANBUS (instead of the dynamixel U2D2/RS485; note there is a similar RS485 version is available as well)
  -   The RollerCAN device is easy to interface to the controller (discussed below) via I2C
  -   The I2C bus is passed through the motor's slip rings allowing chaining without tangling
  -   The I2C bus can be used to attach other I2C devices, including M5Stack's various "Unit" sensors to emulate various end-effectors
  -   The mounting surface and motor mounting interface is "tougher" relative to the dynamixels to improve durability
  -   The RollerCAN impelments https://github.com/scottbez1/smartknob to create magnetic, reconfigurable hatpic "detents" for force feedback
  -   Although the smartknob functions are not trivially exposed by the current M5 implementation, these should be configurable, possibly on the rollercan firmware

- The U2D2 functionality is replaced by an M5 Stack Core3 Controller: https://docs.m5stack.com/en/core/CoreS3

  - The Core3 adds a UI screen, DIN rail mounting, serial/usb, wifi, bluetooth, and a number of other functions
  - The Core3 includes an onboard battery and barrel jack interface (9-24V tolerant) and USB C power interfaces
  - Using the onboard battery (or a supplemental battery) and the Core3 wifi the MG can be completely wireless
  - Initial testing suggests that the system will run in "encoder" mode for 15-20 mins on the Core3 internal battery alone.
  - The Core3 has several firware options for programming, including M5's "UIFLOW" webIDE, which allows for relatively trivial Over-the-air programming
     
- The linkages have been hardened relative to the original GELLO

The following links may be useful to use and expand MG:
CORE3S:
- https://uiflow-micropython.readthedocs.io/en/latest/get-started/index.html

RollerCAN Links:
- https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-RollerCAN%20Lite/Unit-RollerCAN-I2C-Protocol-EN.pdf
- https://uiflow-micropython.readthedocs.io/en/latest/units/rollercan.html
- https://github.com/m5stack/M5Unit-Roller/blob/main/src/unit_rolleri2c.cpp
