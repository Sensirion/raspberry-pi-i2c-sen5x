Getting Started on Raspberry Pi
===============================

This document explains how to set up the Sen55 sensor to run on a Raspberry Pi
using the provided code.

TODO: DRIVER_GENERATOR Add picture of sensor to images/Sen55.png
[<center><img src="images/Sen55.png" width="300px"></center>](TODO: DRIVER_GENERATOR Add evaluation kit URL)

Click [here](TODO: DRIVER_GENERATOR Add evaluation kit URL) to learn more about the SCD4x Sensor and the SCD41 Evaluation Kit Board.


Setup Guide
-----------

### Connecting the Sensor

Your sensor has the four different connectors: VCC, GND, SDA, SCL, SEL. Use
the following pins to connect your Sen55:

 *Sen55*  |    *Raspberry Pi*
 :------: | :------------------:
   VCC    |        Pin 1
   GND    |        Pin 6
   SDA    |        Pin 3
   SCL    |        Pin 5
   SEL    |        Pin 9 TODO: DRIVER_GENERATOR Check if this applies

<center><img src="images/GPIO-Pinout-Diagram.png" width="900px"></center>

### Raspberry Pi

- [Install the Raspberry Pi OS on to your Raspberry Pi](https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up)
- [Enable the I2C interface in the raspi-config](https://www.raspberrypi.org/documentation/configuration/raspi-config.md)
- Download the driver for the [Sensirion Github Page](https://github.com/Sensirion/raspberry-pi-i2c-sen55) and extract the `.zip` on your Raspberry Pi
- Compile the driver
    1. Open a [terminal](https://www.raspberrypi.org/documentation/usage/terminal/?)
    2. Navigate to the driver directory. E.g. `cd ~/raspberry-pi-i2c-sen55`
    3. Run the `make` command to compile the driver

       Output:
       ```
       rm -f sen55_i2c_example_usage
       cc -Os -Wall -fstrict-aliasing -Wstrict-aliasing=1 -Wsign-conversion -fPIC -I. -o sen55_i2c_example_usage  sen55_i2c.h sen55_i2c.c sensirion_i2c_hal.h sensirion_i2c.h sensirion_i2c.c \
       	sensirion_i2c_hal.c sensirion_config.h sensirion_common.h sensirion_common.c sen55_i2c_example_usage.c
       ```
- Test your connected sensor
    - Run `./sen55_i2c_example_usage` in the same directory you used to
      compile the driver.

      Output:
      ```
      TODO: DRIVER_GENERATOR Add sensor output
      ...
      ```

Troubleshooting
---------------

### Initialization failed

-   Ensure that you connected the sensor correctly: All cables are fully
    plugged in and connected to the correct pin.
-   Ensure that I2C is enabled on the Raspberry Pi. For this redo the steps on
    "Enable the I2C interface in the raspi-config" in the guide above.
-   Ensure that your user account has read and write access to the I2C device.
    If it only works with user root (`sudo ./sen55_i2c_example_usage`), it's
    typically due to wrong permission settings.
