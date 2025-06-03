# mello_gello
Improved models and methods for the Gello robot teleop system

![image](https://github.com/user-attachments/assets/da670d3f-2f91-4392-84db-c1f1b88ae2f5)

# MELLO GELLO vs. GELLO

Inspired by and based on the original [GELLO project](https://wuphilipp.github.io/gello_site/).

## Key Improvements

- **Motors:** Uses [ROLLER485](https://shop.m5stack.com/products/rollercan-unit-with-bldc-motor-stm32) for better interface durability, I2C pass-through at similar price point
- **Linkages:** Swaps many fully 3D-printed parts with **Gobuilda 1121 aluminum rail** ([details](https://www.gobilda.com/1121-series-low-side-u-channel)).
- **Controller:** Upgraded from U2D2 to [M5 Stack Core3](https://docs.m5stack.com/en/core/CoreS3) with touchscreen, wireless OTA programming, and expanded connectivity.
- **Wireless:** Core3 onboard battery enables **15-20 min untethered runtime**, WiFi control, and flexible power options.
- **Tool Control:** Supports **any I2C input device**, expanding tool control capabilities.
- **Multi-Function Button:** Uses M5 **Key** to zero rotation or pause movement.

---

## Versions:

### UR5e:
The UR5 version of MG is *AVAILABLE* in the Universal Robots/UR5e folder - https://github.com/emmarUW/mello_gello/blob/main/Universal%20Robots/UR5e/README.md

### Franka:
The Franka version of MG is *IN WORK* - in the Franka folder
