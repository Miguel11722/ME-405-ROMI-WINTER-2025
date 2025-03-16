# ME-405-ROMI

# Table of Contents

[Overview](#Overview)

[Videos](#videos)

[Tasks](#Tasks)
- [gcTask](#gcTask)
- [imuTask](#imuTask)
- [bumpTask](#bumpTask)
- [leftTask](#leftTask)
- [lineTask](#lineTask)
- [rightTask](#rightTask)

[Classes](#Classes)
- [BumpSensor](#BumpSensor)
- [Encoder](#Encoder)
- [IMU](#IMU)
- [LineSensor](#LineSensor)
- [Motor](#Motor)
	

[Appendix](#Appendix)

# Overview



# Videos

[Run 1](https://youtu.be/CR8xlK-HHFw)

[Run 2](https://youtu.be/JZjPs5Mh1RU)

# Tasks

These are the tasks run by the scheduler in the main file. Each gets passed a tuple of shares by the scheduler when run. These shares are:
- **batLevel:** The current voltage of the battery. Shared between leftTask and rightTask.
- **bumped:** Shares whether or not the bump sensors have been pressed. Shared between bumpTask, leftTask, and rightTask
- **centroid:** The most recently updated centroid reading from the line sensor. Shared between lineTask, leftTask, and rightTask
- **east:** The initial IMU heading reading when main is run. Shared between imuTask, leftTask, and rightTask.
- **heading:** The most recently updated IMU heading reading. Shared between imuTask, leftTask, and rightTask.
- **lineType:** The most recently updated type of line the line sensor read. Shared between lineTask, leftTask, and rightTask
- **stage:** The current stage of the course. This allows the left and right tasks to be in the same stage and not get out of sync. Shared between leftTask, rightTask and bumpTask.

The tasks here are indexed by their file name rather than class name for ease of understanding which task does what. The class name is included in the task description. Each task also has a finite state diagram in its description.

The task diagram is shown below.

![Task Diagram for ME 405 term project](TaskDiagram.png)

## gcTask

**Finite State Diagram:**

![Finite State Diagram for gcTask](gcTaskFSM.png)

**Description:**

Period:
Priority:

**Class Name:** collector

## imuTask

**Finite State Diagram:**

![Finite State Diagram for imuTask](imuTaskFSM.png)

**Description:**

Period:
Priority:

**Class Name:** BNO

## bumpTask

**Finite State Diagram:**

![Finite State Diagram for bumpTask](bumpTaskFSM.png)

**Description:**

**Class Name:** Bump

## leftTask

**Finite State Diagram:**

![Finite State Diagram for leftTask](leftTaskFSM.png)

**Description:**

Period:
Priority:

**Class Name:** leftMotor

## lineTask

**Finite State Diagram:**

![Finite State Diagram for lineTask](lineTaskFSM.png)

**Description:**

Period:
Priority:

**Class Name:** lineSensor

## rightTask

**Finite State Diagram:**

![Finite State Diagram for rightTask](rightTaskFSM.png)

**Description:**

Period:
Priority:

**Class Name:** rightMotor

# Classes

Each class is described below, with links to the corresponding file. The classes are indexed by class name, with the file name included in the task description.

## BumpSensor

**Description:** A driver for the bump sensors on a Pololu Romi robot.

**File Name:** bumpTask.py

## Encoder

**Description:** A driver for the encoders on a Pololu Romi robot.

**File Name:** encoder.py

## IMU

**Description:** A driver for an Adafruit BNO055 IMU.

**File Name:** BNO055.py

## LineSensor

**Description:** A driver for a 7 channel analog line sensor array from Pololu.

**File name:** analoglinesensor

## Motor

**Description:** A driver for the motors on a Pololu Romi robot.

**File Name:** motor.py

# Appendix
