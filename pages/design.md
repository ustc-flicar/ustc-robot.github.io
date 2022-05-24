---
layout: page-fullwidth
show_meta: false
title: "Sensors & Usage"
#subheadline: "Layouts of Feeling Responsive"
header:
   image_fullwidth: "header_unsplash_5.jpg"
permalink: "/design/"
---
## Overview

The sensor setup is illustrated in [Fig. 1](#fig-harware). The corresponding ROS topics are reported in [Tab. 1](#tab-sensor-and-topic).

<table>
 <td width="40%">
 <table>
	<tr>
	    <th>Platform</th>
	</tr >
	<tr>
      <td rowspan="5"><img src="../images/Okapia _platform.png" width="97%"/></td>
	</tr>
</table>
<table>
	<tr>
	    <th>Vehicle</th>
          <th>Pic</th> 
	</tr >
	<tr>
      <td width="30%">Husky A200</td>
      <td><img src="../images/Husky_dipan.jpg" width="60%"/></td>
	</tr>
</table>
</td>
<td>
 <table>
 <thead>
	<tr>
      <th>Sensor</th>
      <th>type</th> 
      <th>Rate</th>
      <th>Pics</th>
	</tr >
  </thead>
	<tr>
      <td width="25%">INS/IMU</td>
      <td width="30%">Xsens MTi-G-710</td>
      <td width="15%">400 Hz</td>
      <td><img src="../images/xsens.jpg" width="30%"/></td>
	</tr>
      <tr >
      <td width="25%">Horizontal Lidar</td>
      <td width="30%">Velodyne HDL-32E</td>
      <td width="10%">10 Hz</td>
      <td><img src="../images/Velodyne_32e.png" width="30%"/></td>
	</tr>
	<tr>
	    <td width="25%">Vertical Lidar</td>
      <td width="30%">Velodyne VLP-32C</td>
      <td width="10%">10 Hz</td>
      <td><img src="../images/Velodyne_Ultrapuck.png" width="30%"/></td>
	</tr>
	<tr>
	    <td width="25%">MEMS Lidar</td>
      <td width="30%">LiVOX Avia</td>
      <td width="10%">10 Hz</td>
      <td><img src="../images/LiVOX_Avia.jpg" width="30%"/></td>
	</tr>
	<tr>
	    <td width="25%">Stereo Camera front</td>
      <td width="30%">PointGrey BBX3-13S2C-38</td>
      <td width="10%">10 Hz</td>
      <td><img src="../images/bumblebee_xb3.jpg" width="40%"/></td>
	</tr>
      <tr>
	    <td width="25%">Stereo Camera back</td>
      <td width="30%">PointGrey BBX2-08S2C-38</td>
      <td width="10%">10 Hz</td>
      <td><img src="../images/bumblebee_xb2.jpg" width="30%"/></td>
	</tr>
	<tr>
	     <td width="25%">Mono Camera 1<br>(with VLP-32C)</td>
      <td width="30%">PointGrey CLMN-13S2C-CS</td>
      <td width="10%">10 Hz</td>
      <td><img src="../images/CMLN-13S2C-CS.jpg" width="30%"/></td>
	</tr>
	<tr>
	     <td width="25%">Mono Camera 2<br>(with HDL-32E)</td>
      <td width="30%">Hikvision MV-CB016-10GC-C</td>
      <td width="10%">20 Hz</td>
      <td><img src="../images/Hikvision_MV-CB016-10GC-C.png" width="40%"/></td>
	</tr>
      <tr>
      <td width="25%">Mono Camera 3<br>(with LiVOX Avia)</td>
      <td width="30%">Hikvision MV-CE060-10UC</td>
      <td width="10%">20 Hz</td>
      <td><img src="../images/Hikvision MV-CE060-10UC.png" width="30%"/></td>
	</tr>
</table>
</td>
</table>

## IMU
The IMU we use is Xsens MTi-G-710. It is a 9-DoF inertia sensor which gives roll, pitch, and yaw estimatio. 9-DoF IMU data is necessarily for some slam algorithms such as <a href="https://github.com/TixiaoShan/LIO-SAM">LIO-SAM</a>, our data can meet the requirment.


For more information of Xsens MTi-G-710：
<a href="../pdf/MTi_usermanual.pdf">User Manual of Xsens_MTi</a>

<table><tr>
<td><img src="../images/xsens.jpg" alt="Hardware Setup" width="50%"/></td>
<td><img src="../images/xsens_zuobiaoxi.png" width="80%"></td>
</tr></table>
<p style="text-align: center;">Fig 2. The IMU frame of reference </p> <a name="fig-hardware"></a>

## Mechanical Lidar
### Horizontal Lidar 1
The first horizontal Lidar in the middle of the multisensors platform is Velodyne HDL-32E.
<a href="../pdf/MANUAL_USERS_HDL32E.pdf">User Manual of Velodyne_HDL_32E</a>

```cpp
struct PointXYZIRT
{
    PCL_ADD_POINT4D
    PCL_ADD_INTENSITY;
    uint16_t ring;
    float time;
    EIGEN_MAKE_ALIGNED_OPERATOR_NEW
} EIGEN_ALIGN16;

POINT_CLOUD_REGISTER_POINT_STRUCT (PointXYZIRT,  
                                    (float, x, x) 
                                    (float, y, y) 
                                    (float, z, z) 
                                    (float, intensity, intensity)
                                    (uint16_t, ring, ring) 
                                    (float, time, time))
```
### Vertical Lidar
垂直方向的激光雷达型号是Velodyne VLP-32C(Ultra Puck), The VLP-32C sensor uses 32 infra-red (IR) lasers paired with IR detectors to measure distances to objects. The device is mounted securely within a compact, weather-resistant housing. The assembly of laser/detector pairs spins rapidly within
its fixed housing to scan the surrounding environment, firing pairs of lasers approximately 18,000 times per second, providing, in real-time, a rich set of 3D point data.

### Horizontal Lidar 2
The second horizontal Lidar in the middle of the multisensors platform is Ouster OS0-128.

```cpp
struct PointXYZIRT
{
    PCL_ADD_POINT4D;
    float intensity;
    uint32_t t;
    uint16_t reflectivity;
    uint8_t  ring;          // The channel index
    uint16_t noise;
    uint32_t range;         // The distance measurement
    EIGEN_MAKE_ALIGNED_OPERATOR_NEW
} EIGEN_ALIGN16;

POINT_CLOUD_REGISTER_POINT_STRUCT(PointXYZIRT,
                                  (float, x, x)
                                  (float, y, y)
                                  (float, z, z)
                                  (float, intensity, intensity)
                                  (uint32_t, t, t)
                                  (uint16_t, reflectivity, reflectivity)
                                  (uint8_t,  ring, ring)
                                  (uint16_t, noise, noise)
                                  (uint32_t, range, range))
```

## MEMS Lidar
We Use DJI LiVOX Avia Lidar in our dataset. It

Livox customized data package format, as follows:
```cpp
Header header             # ROS standard message header
uint64 timebase           # The time of first point
uint32 point_num          # Total number of pointclouds
uint8  lidar_id           # Lidar device id number
uint8[3]  rsvd            # Reserved use
CustomPoint[] points      # Pointcloud data
```
Customized Point Cloud (CustomPoint) format in the above customized data package:
```cpp
uint32 offset_time      # offset time relative to the base time
float32 x               # X axis, unit:m
float32 y               # Y axis, unit:m
float32 z               # Z axis, unit:m
uint8 reflectivity      # reflectivity, 0~255
uint8 tag               # livox tag
uint8 line              # laser number in lidar
```

## Stereo Cameras
There are three Stereo Cameras: Bumblebee_xb3(Frount View),Bumblebee_xb2(Back view) and ZED 2i(Below view).

## Mono Cameras

## Laser Tracker
The ground truth of our dataset is provided by API T3 Laser Tracker.
<a href="https://www.adm3d.com/Home/T3Tracker">https://www.adm3d.com/Home/T3Tracker</a>

<img src="../images/API_T3_Laser_Tracker.png" width="100%"/>