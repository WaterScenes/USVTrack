# USVTrack

<h4>A 4D Radar-Camera Tracking Dataset for Autonomous Driving in Inland Waterways</h4>

* Website: 
* arXiv: 


## Overview
- [Changelog](#changelog)
- [Dataset](#dataset)
- [Devkit](#devkit)
- [Acknowledgement](#acknowledgement)
- [Citation](#citation)

## Changelog

## Dataset
### Introduction

### Dataset Statistics


### Dataset Structure

```
WaterScenes-Tracking (root)
  - image # RGB images
    - 000001.jpg
  - radar # radar files
    - 000001.csv
  - calib # intrisic and extrisic parameters
    - 000001.txt
  - gps # gps file
    - 000001.csv
  - imu # imu file
    - 000001.csv
  - label # annotation files for
    - yolo 
      - 000001.txt


```

### Tracking GT file
| Column | Label      | Note                                               |
|------|------------|----------------------------------------------------|
| 1    | Frame number       |   start from 1                                                 |
| 2    | Indentity number       |           start from 1                                         |
| 3, 4, 5, 6    | Box left, top, width, height     |                                                    |
| 7    | Confidence score      |                                                    |
| 8    | Class     |  Refer to [Class](#Class)                                                  |
| 9    | Visibility      |                                                    |

### Det file
| Column | Label      | Note                                               |
|------|------------|----------------------------------------------------|
| 1    | Frame number       |                                                    |
| 2    | Indentity number   | -1                                                   |
| 3, 4, 5, 6    | Box left, top, width, height     |                                                    |
| 7    | Confidence score      |                                                    |
| 8    | Class     |  Refer to [Class](#Class)                                                  |
| 9    | Visibility      |  -1

### Class
| Code | Label      | Note                                               |
|------|------------|----------------------------------------------------|
| 0    | ship       |                                                    |
| 1    | boat       |                                                    |
| 2    | vessel     |                                                    |
| -1   | no-object  | only for radar point clouds                        |

### Radar Format
Radar point clouds are stored in csv files.
Each csv file contains a set of points in a specific timestamp:
| Column        | Description                                                     |
|---------------|-----------------------------------------------------------------|
| timestamp     | timestamp of the point                                          |
| range         | radial distance to the detection (in m)                         |
| doppler       | radial velocity measured for this point (in m/s)                |
| azimuth       | azimuth angle to the detection (in degree)                      |
| elevation     | elevation angle to the detection (in degree)                    |
| power         | reflected power value of the detection (in dB)                  |
| x             | x value in the XYZ coordinates                                  |
| y             | y value in the XYZ coordinates                                  |
| z             | z value in the XYZ coordinates                                  |
| comp_height   | absolute height of the point (in m)                             |
| comp_velocity | absolute velocity of the point (in m/s)                         |
| u             | x-axis on the image plane                                       |
| v             | y-axis on the image plane                                       |
| label         | class label of this point (Refer to [Class](#Class))            |
| instance      | instance id of this point (0 is for no-object)                  |


### GPS Format

| Column                  | Description                            |
|-------------------------|----------------------------------------|
| timestamp               | current timestamp                      |
| latitude                | latitude                               |
| longitude               | longitude                              |
| number_of_satellites    | number of satellites                   |
| altitude                | altitude                               |
| true_north_heading      | true north heading to the earth        |
| magnetic_north_heading  | magnetic north heading to the earth    |
| ground_speed_kn         | speed (in kn)                          |
| ground_speed_kph        | speed (in km/h)                        |

### IMU Format

| Column                | Description                            |
|-----------------------|----------------------------------------|
| timestamp             | current timestamp                      |
| pitch                 | pitch (x-axis, right)                  |
| roll                  | roll (y-axis, front)                   |
| yaw                   | yaw (z-axis, top)                      |
| angular_velocity_x    | angular velocity in x-axis             |
| angular_velocity_y    | angular velocity in y-axis             |
| angular_velocity_z    | angular velocity in z-axis             |
| linear_velocity_x     | linear velocity in x-axis              |
| linear_velocity_y     | linear velocity in y-axis              |
| linear_velocity_z     | linear velocity in z-axis              |
| magnetic_field_x      | magnetic field strength in x-axis      |
| magnetic_field_y      | magnetic field strength in y-axis      |
| magnetic_field_z      | magnetic field strength in z-axis      |



