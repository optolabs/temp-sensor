# Temperature sensing through graphical representation and data storage

Configuring a temperature sensor with appropriate connections to Raspberry Pi for accurate readings at specific time stamps, and graphing data as well as writing it to a json file.


## Authors

Project by Maia Nieves.
See citations for the resources used.

## Materials Used
-Raspberry Pi 4
-Waterproof 1-Wire DS18B20 Compatible Digital temperature sensor
-3xFemale-to-male Dupont Wire
-4.7k resistor


## Hardware Assembly

The images below from circuitbasics gives the necessary connections for ssh terminal output.
For the DS18B20:
The red wire is Vcc
The black wire is GND
The yellow wire is DATA
![Temp sensor labelling](https://www.circuitbasics.com/wp-content/uploads/2016/03/Raspberry-Pi-DS18B20-Tutorial-DS18B20-Pinout-Diagram-300x293.png)


![Setup for temp sensor](https://www.circuitbasics.com/wp-content/uploads/2016/03/Raspberry-Pi-DS18B20-768x337.png)

## ENABLE THE ONE-WIRE INTERFACE

We’ll need to enable the One-Wire interface before the Pi can receive data from the sensor. Once you’ve connected the DS18B20, power up your Pi and log in, then follow these steps to enable the One-Wire interface:

1. At the command prompt, enter  `sudo nano /boot/config.txt`, then add this to the bottom of the file:

`dtoverlay=w1-gpio`

2. Exit Nano, and reboot the Pi with  `sudo reboot`

3. Log in to the Pi again, and at the command prompt enter `sudo modprobe w1-``gpio`

4. Then enter `sudo modprobe w1-therm`

5. Change directories to the /sys/bus/w1/devices directory by entering `cd /sys/bus/w1/devices`

6. Now enter  `ls`  to list the devices:

![Raspberry Pi DS18B20 Temperature Sensor Tutorial - One Wire Device Address](https://www.circuitbasics.com/wp-content/uploads/2016/03/Raspberry-Pi-DS18B20-Temperature-Sensor-Tutorial-One-Wire-Device-Address.png)



7. Now enter `cd 28-XXXXXXXXXXXX` (change the X’s to your own address)


8. Enter `cat w1_slave`  which will show the raw temperature reading output by the sensor:

![Raspberry Pi DS18B20 Temperature Sensor Tutorial - DS18B20 Raw Output](https://www.circuitbasics.com/wp-content/uploads/2016/03/Raspberry-Pi-DS18B20-Temperature-Sensor-Tutorial-DS18B20-Raw-Output.png)

Here the temperature reading is `t=28625`, which means a temperature of 28.625 degrees Celsius.

## Citations
- https://www.circuitbasics.com/raspberry-pi-ds18b20-temperature-sensor-tutorial/
- https://www.digikey.com/en/maker/projects/graph-sensor-data-with-python-and-matplotlib/93f919fd4e134c48bc5cd2bc0e5a5ba2
- https://learn.sparkfun.com/tutorials/graph-sensor-data-with-python-and-matplotlib/update-a-graph-in-real-time

