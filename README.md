# mello_gello
Improved models and methods for the Gello robot teleop system

![image](https://github.com/user-attachments/assets/da670d3f-2f91-4392-84db-c1f1b88ae2f5)


This project is heavily inspired by uses code derived from the original GELLO project - https://wuphilipp.github.io/gello_site/

MELLO GELLO (MG) overhauls the GELLO design and replaces hardware components 
- In place of the dynamixels used in the original GELLO, MG uses "ROLLER485" motors from M5 stack: https://shop.m5stack.com/products/rollercan-unit-with-bldc-motor-stm32
- The Roller485 device includes a BLDC motor and an encoder addressible via I2C or RS485 (instead of the dynamixel U2D2/RS485; note there is a similar CAN version is available as well whcih )
  -   The Roller485 device is easy to interface to the controller (discussed below) via I2C
  -   The I2C bus is passed through the motor's slip rings allowing chaining without tangling/360 degree rotation
  -   The I2C bus can be used to attach other I2C devices, including M5Stack's various "Unit" sensors to emulate various end-effectors
  -   The mounting surface and motor mounting interface is "tougher" relative to the dynamixels to improve durability
  -   The Roller485 impelments https://github.com/scottbez1/smartknob to create magnetic, reconfigurable hatpic "detents" for force feedback (although the smartknob functions are not trivially exposed by the current M5 implementation, these should be configurable, possibly on the roller485 firmware)

- The U2D2 functionality is replaced by an M5 Stack Core3 Controller: https://docs.m5stack.com/en/core/CoreS3

  - The Core3 adds a UI screen, DIN rail mounting, serial/usb, wifi, bluetooth, and a number of other functions
  - The Core3 includes an onboard battery and barrel jack interface (9-24V tolerant) and USB C power interfaces
  - Using the onboard battery (or a supplemental battery) and the Core3 wifi the MG can be completely wireless
  - Initial testing suggests that the system will run in "encoder" mode for 15-20 mins on the Core3 internal battery alone.
  - The Core3 has several firware options for programming, including M5's "UIFLOW" webIDE, which allows for relatively trivial Over-the-air programming
    
- The linkages have been hardened relative to the original GELLO
  - Where feasible, "Gobuilda" 1121 series aluminum rail is usesd in place of fully 3D printed structure.
  - Beyond being physically more robust, the rail is available in pre-cut 24mm increments (https://www.gobilda.com/1121-series-low-side-u-channel) so that minor geometry differences (such as those in the relative length of UR arm link lengths) across robot types can be accomadated while re-using many parts.
  

The following links may be useful to use and expand MG:
CORE3S:
- https://uiflow-micropython.readthedocs.io/en/latest/get-started/index.html

RollerCAN Links:
- https://docs.m5stack.com/en/guide/motor_ctl/rollercan/rollercan
- https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-RollerCAN%20Lite/Unit-RollerCAN-I2C-Protocol-EN.pdf
- https://uiflow-micropython.readthedocs.io/en/latest/units/rollercan.html
- https://github.com/m5stack/M5Unit-Roller/blob/main/src/unit_rolleri2c.cpp
