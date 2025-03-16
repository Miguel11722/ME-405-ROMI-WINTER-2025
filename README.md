
## Overview

### Table of Contents
[Videos](#videos)

[Classes](#Classes)

	[LineSensor](#LineSensor)
	
[Tasks](#Tasks)

[Appendix](#Appendix)


## Videos

[Run 1](https://youtu.be/CR8xlK-HHFw)

[Run 2](https://youtu.be/JZjPs5Mh1RU)

## Classes

Each class is described below, with links to the corresponding file.

### LineSensor

**Description:** This is a driver for a 7 channel analog line sensor array from Pololu.

**File name:** analoglinesensor

**Methods:**
- LineSensor.init(CTRL,pin1,pin3,pin5,pin7,pin9,pin11,pin13): Initializes the line sensor.
	- CTRL is the control pin
	- pin1, pin3, etc. are the pins corresponding to the line sensor channels
- LineSensor.calibrate(): Calibrates the line sensor white and black readings. This should only be run for debugging and testing purposes, and the desired calibration data should be coded in the initialization method. For us, that meant coding the array of black values to 300, since we found that to be around the lowest the line sensor would read while over the line in our final track.
- LineSensor.update(): Updates the line sensor readings. Calls LineSensor.solve_centroid() and LineSensor.solve_lineType()
- LineSensor.get_sensors(): Returns a list of the most recently updated sensor readings.
- LineSensor.get_centroid(): Returns the centroid value from the most recent update.
- LineSensor.get_lineType(): Returns the line type as an integer as determined from the most recent update.
	- lineType = 1: Normal line.
	- lineType = 2: All readings are white.
	- lineType = 3: 5 or more sensors read black.
- LineSensor.solve_centroid(): Takes the most recently updated line sensor readings and returns the centroid of the line sensor as a value away from 0, where 0 is the middle of the sensor. Negative centroid values indicate that the centroid is in the first half of the sensors (1-5) whereas positive centroid values indicate that the centroid is in the second half of the sensors (9-13).
- LineSensor.solve_lineType(): Solves and returns the type of line as determined from the most recently updated line sensor readings.
	- lineType = 1: Normal line.
	- lineType = 2: All readings are white.
	- lineType = 3: 5 or more sensors read black.
### IMU

**Description:**

**File Name:** BNO055.py

**Methods:**

### Bump

**Description:**

**File Name:** bumpTask.py

**Methods:**

### Encoder

**Description:**

**File Name:** encoder.py

**Methods:**

### Motor

**Description:**

**File Name:** motor.py

**Methods:**


## Tasks

### collector

**Description:**

**File Name:** gcTask.py

**Methods:**

### BumpSensor

**Description:**

**File Name:** bumpsensor.py

**Methods:**

### BNO

**Description:**

**File Name:** imuTask.py

**Methods:**

### BumpSensor

**Description:**

**File Name:** bumpsensor.py

**Methods:**

### leftMotor

**Description:**

**File Name:** leftTask.py

**Methods:**

### lineSensor

**Description:**

**File Name:** lineTask.py

**Methods:**

### rightMotor

**Description:**

**File Name:** rightTask.py

**Methods:**

## Appendix
