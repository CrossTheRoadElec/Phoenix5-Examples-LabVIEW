# CANifier Demo
The CANifier Demo project is an example that demonstrates some of the use cases of the CANifier. The CANifier is a CAN-controlled multipurpose LED and General Purpose Input/Output (GPIO) controller. It supports a variety of sensors that communicate through Quadrature, Limit Switch, SPI, I2c, and PWM Input/Output. With the Three low-side outputs, we are able to control any common RGB LED strip. The project also uses PWM inputs to communicate with a LIDAR Lite V3 sensor. Lastly, this project provides insight on how the new CTRE framework works and gives an example to how classes, schedulers, and organization works. 

# The Project's Software
For how to assemble the physical project, refer to the section below "The Project's Hardware".

Before deploying the project to the RoboRIO, we need to make sure we have the correct firmware. The example was built using CTRE's Alpha build of the Phoenix Framework, which can be found on the [HERO's technical resources page][5]. Once the installer has been ran, it will be important to ensure all hardware has been flashed with the latest firmware.

The project operates in one mode with LED strip, PWM motor controller, and LIDAR Lite V3 sensor all displaying the CANifier's features. The gamepad's right joystick controls the red and blue values of LED strip while the left joystick controls the PWM motor controller output going from -1 to 1 using the Y-axis. The LIDAR sensor controls the green value of the LED strip, where near distance detection will output a lower or dimmer value for green while far distance detection will output a higher or brighter value for green.

Below are a few screenshots of the example project

#### Creating and Initializing CANifier
![alt text][code 1]

#### Grabbing Joystick values for red and blue values
![alt text][code 2]

#### Pulling PWM signals and using LIDAR Lite V3 for green value
![alt text][code 4]

#### CANifier outputing RGB values generated from above code blocks to LED strip
![alt text][code 5]

#### PWM motor controller controlled by left joystick of gamepad
![alt text][code 3]

# The Project's Hardware
This example project requires a [CANifier][2], [LIDAR Lite V3][3], [gamepad][4], RoboRIO, PWM motor controller, any common RGB LED Strip, and power source such as a power supply.

It is recommended that the user should test the CANifier in isolation prior to installation. It would also be the best opportunity for the user to field-upgrade the CANifier, test peripherals, and ensure wiring is correct. 

For transmitting signals, the CANifier is connected to both the LED strip and PWM motor controller. The LED Strip is wired to the CANifier's four pins on the labeled, A, B, C, and V+, which can be seen below in Figure 1.

#### Figure 1: LED strip wired to the CANifier, R to A, G to B, B to C, and + to V+.
![alt text][LED Strip]

The PWM motor controller’s PWM signal is wired directly to the CANifier. Wire the PWM motor controller’s ground to one of the ground pins available and connect the PWM wire (typically denoted by a white wire) to one of the 3 PWM outputs. As of Phoenix Toolsuite 5.0.3.3 Installer, PWM I/O pin 4 can only be used an input.

For retrieving signals, the project has a LIDAR Lite V3 Distance Sensor communicating with the CANifier through PWM. To wire the LIDAR Lite V3 to the CANifier, follow the steps below and use the Figure 2 as a guide. Note: The LIDAR Lite V3 is not required to use the example, but only enhances the user’s experience.

#### Figure 2: LIDAR Lite V3 wired to the CANifier. Steps with order explained in table.
![alt text][LIDAR]

The CANifier can then be connected to the RoboRIO through CAN. Once all connections to the CANifier has been made, it is recommended that it be insulted in a 1" heat shrink tubing as seen below in the Figure 3.

#### Figure 3: Heat shrink to insulate CANifier from shorts
![alt text][Insulation]

##### Further instructions on how to use and wire the CANifier can be found within the documentation, which can be found here. [http://www.ctr-electronics.com/can-can-canifier-driver-led-driver-gpio.html#product_tabs_technical_resources]

### Example Setup
Below is a sample setup containing all the hardware required. A PWM motor controller was not available for use at the time, so we modified the TalonSRX to become a PWM motor Controller. Below in Figure 4, we have the physical setup used to run the CANifier Demo project. 

#### Figure 4: Example Setup of all the hardware connected to each other
![alt text][Setup]

# Troubleshoot
### CANifier or Gamepad not recognized?
This may be due to having mismatched device ID's to the software. Users have two options. They may change the device ID to match the software or provide the correct device ID within begin.vi.

#### In the image below, CANifier is being constructed with device ID of 0
![alt text][code 6]




 [1]: http://www.ctr-electronics.com/hro.html#product_tabs_technical_resources
 [2]: http://www.ctr-electronics.com/can-can-canifier-driver-led-driver-gpio.html
 [3]: https://www.sparkfun.com/products/14032
 [4]: http://www.andymark.com/product-p/am-2064.htm
 [5]: http://www.ctr-electronics.com/hro.html#product_tabs_technical_resources
 [LED Strip]: https://github.com/CrossTheRoadElec/Phoenix-Examples-Languages/blob/gh-doc/Java/CANifier%20Demo/Documentation/Capture2.PNG
 [LIDAR]: https://github.com/CrossTheRoadElec/Phoenix-Examples-Languages/blob/gh-doc/Java/CANifier%20Demo/Documentation/Capture.PNG
 [Insulation]: https://github.com/CrossTheRoadElec/Phoenix-Examples-Languages/blob/gh-doc/Java/CANifier%20Demo/Documentation/IMG_20171011_103615.jpg
 [Setup]: https://github.com/CrossTheRoadElec/Phoenix-Examples-Languages/blob/gh-doc/Java/CANifier%20Demo/Documentation/IMG_20171011_103545.jpg
 [More Pretty]: https://github.com/CrossTheRoadElec/Phoenix-Examples-Languages/blob/gh-doc/Java/CANifier%20Demo/Documentation/IMG_20171011_125250.jpg
 [Final Image]: https://github.com/CrossTheRoadElec/Phoenix-Examples-Languages/blob/gh-doc/Java/CANifier%20Demo/Documentation/IMG_20171011_130436.jpg
 
 [code 1]: https://github.com/CrossTheRoadElec/Phoenix-Examples-LabVIEW/blob/gh-doc/CANifier%20Demo/Documentation/Block%204.PNG
 [code 2]: https://github.com/CrossTheRoadElec/Phoenix-Examples-LabVIEW/blob/gh-doc/CANifier%20Demo/Documentation/Block%202.PNG
 [code 3]: https://github.com/CrossTheRoadElec/Phoenix-Examples-LabVIEW/blob/gh-doc/CANifier%20Demo/Documentation/Block%203.PNG
 [code 4]: https://github.com/CrossTheRoadElec/Phoenix-Examples-LabVIEW/blob/gh-doc/CANifier%20Demo/Documentation/Block%201.PNG
 [code 5]: https://github.com/CrossTheRoadElec/Phoenix-Examples-LabVIEW/blob/gh-doc/CANifier%20Demo/Documentation/LEDOutput.PNG
 [code 6]: https://github.com/CrossTheRoadElec/Phoenix-Examples-LabVIEW/blob/gh-doc/CANifier%20Demo/Documentation/CANifierDemoLV.PNG
