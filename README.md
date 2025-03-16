
## Table of Contents

[Overview](#Overview)

[Videos](#videos)

[Classes](#Classes)
- [Bump](#Bump)
- [Encoder](#Encoder)
- [IMU](#IMU)
- [LineSensor](#LineSensor)
- [Motor](#Motor)
	
[Tasks](#Tasks)
- [gcTask](#gcTask)
- [imuTask](#imuTask)
- [bumpTask](#bumpTask)
- [leftTask](#leftTask)
- [lineTask](#lineTask)
- [rightTask](#rightTask)

[Appendix](#Appendix)

## Overview

## Videos

[Run 1](https://youtu.be/CR8xlK-HHFw)

[Run 2](https://youtu.be/JZjPs5Mh1RU)

## Classes

Each class is described below, with links to the corresponding file.

### Bump

**Description:**

**File Name:** bumpTask.py

**Methods:**

### Encoder

**Description:**

**File Name:** encoder.py

**Methods:**

### IMU

**Description:**

**File Name:** BNO055.py

**Methods:**

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

### Motor

**Description:**

**File Name:** motor.py

**Methods:**

## Tasks

These are the tasks run by the scheduler in the main file. Each gets passed a tuple of shares by the scheduler when run.

The tasks here are indexed by their file name rather than class name for ease of understanding which task does what. The class name used in main is included in the task description.

### gcTask

**Description:**

Period:
Priority:

**Class Name:** collector

**Methods:**

### imuTask

**Description:**

Period:
Priority:

**Class Name:** BNO

**Methods:**

### bumpTask

**Description:**

**Class Name:** Bump

**Methods:**

### leftTask

**Description:**

Period:
Priority:

**Class Name:** leftMotor

**Methods:**

### lineTask

**Description:**

Period:
Priority:

**Class Name:** lineSensor

**Methods:**

### rightTask

**Description:**

Period:
Priority:

**Class Name:** rightMotor

**Methods:**

## Appendix
