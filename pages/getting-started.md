---
layout: page-fullwidth
title: "Acquisition System"
header:
   image_fullwidth  : "header_homepage_13.jpg"
permalink           : "/getting-started/"
sort: 1
---
## Overview

The acquisition system is illustrated in [Fig. 1](#fig-acsystme_1). It consists with three parts: Bucket Truck, Multisensors Platform and Ground Truth System.The bucket truck uses a hydraulic arm to lift the multi-sensor data acquisition system into the air. Well-calibrated and well-synchronized sensors such as cameras, Lidars, and IMUs collect multimodal data of the environment and motion information of the end of hydraulic arm. The laser tracker on the ground tracks the target prism on the motion platform, which provides millimeter-accurate 3D motion trajectories to provide benchmarks for positioning tasks.
<!-- 
斗式卡车使用液压臂将多传感器数据采集系统提升到空中，标定和同步良好的相机、激光雷达和IMU等传感器收集运动信息及多模态环境数据，地面的激光追踪仪对运动平台的靶球进行跟踪，提供毫米精度的三维运动轨迹，为定位任务提供基准
-->
<a name="fig-acsystme_1"></a>
<p align="center">
    <img src="../images/acquisition_page1.jpg" alt="Hardware Setup" width="70%"/>
</p>
<p style="text-align: center;">Fig 1. "Giraffe" Acquisition System </p>


## Bucket Truck

Our bucket Truck is <a href="../_layouts/xg_en_bucket_truck.html">XCMG-XGS5143JGKZ</a>
The sensor setup is illustrated in [Fig. 1](#fig-harware). The corresponding ROS topics are reported in [Tab. 1](#tab-sensor-and-topic).

<a name="fig-hardware"></a>
<p align="center">
    <img src="../images/hardware.jpg" alt="Hardware Setup" width="50%"/>
</p>
<p style="text-align: center;">Fig 1. The research UAV with its sensors and corresponding coordinate frames </p>

<br>

<a name="tab-sensor-and-topic"></a>
<p style="text-align: center;">Table 1. Sensors and their ROS topics</p>
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:middle}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:middle}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-c3ow">No.</th>
    <th class="tg-c3ow">Sensor</th>
    <th class="tg-c3ow">Manufacturer<br>&amp; Product name</th>
    <th class="tg-c3ow">ROS topic name</th>
    <th class="tg-c3ow">Message Type</th>
    <th class="tg-c3ow">Nominal Rate</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-c3ow" rowspan="3">1</td>
    <td class="tg-c3ow" rowspan="3">IMU</td>
    <td class="tg-c3ow" rowspan="3">VectorNav<br>VN100</td>
    <td class="tg-0pky">/imu/imu</td>
    <td class="tg-0pky">sensor_msgs/Imu</td>
    <td class="tg-c3ow">385 Hz</td>
  </tr>
  <tr>
    <td class="tg-0pky">/imu/magnetic_field</td>
    <td class="tg-0pky">sensor_msgs/MagneticField</td>
    <td class="tg-c3ow">385 Hz</td>
  </tr>
  <tr>
    <td class="tg-0pky">/imu/temperature</td>
    <td class="tg-0pky">sensor_msgs/Temperature</td>
    <td class="tg-c3ow">385 Hz</td>
  </tr>
  <tr>
    <td class="tg-c3ow" rowspan="2">2</td>
    <td class="tg-c3ow" rowspan="2">Horizontal Lidar</td>
    <td class="tg-c3ow" rowspan="2">Ouster<br>OS1-16 gen 1</td>
    <td class="tg-0pky">/os1_cloud_node1/imu</td>
    <td class="tg-0pky">sensor_msgs/Imu</td>
    <td class="tg-c3ow">100 Hz</td>
  </tr>
  <tr>
    <td class="tg-0pky">/os1_cloud_node1/points</td>
    <td class="tg-0pky">sensor_msgs/PointCloud2</td>
    <td class="tg-c3ow">10 Hz</td>
  </tr>
  <tr>
    <td class="tg-c3ow" rowspan="2">3</td>
    <td class="tg-c3ow" rowspan="2">Vertical Lidar</td>
    <td class="tg-c3ow" rowspan="2">Ouster<br>OS1-16 gen 1</td>
    <td class="tg-0pky">/os1_cloud_node2/imu</td>
    <td class="tg-0pky">sensor_msgs/Imu</td>
    <td class="tg-c3ow">100 Hz</td>
  </tr>
  <tr>
    <td class="tg-0pky">/os1_cloud_node2/points</td>
    <td class="tg-0pky">sensor_msgs/PointCloud2</td>
    <td class="tg-c3ow">10 Hz</td>
  </tr>
  <tr>
    <td class="tg-c3ow">4</td>
    <td class="tg-c3ow">Camera 1</td>
    <td class="tg-c3ow">uEye 1221 LE<br>(monochome)</td>
    <td class="tg-0pky">/left/image_raw</td>
    <td class="tg-0pky">sensor_msgs/Image</td>
    <td class="tg-c3ow">10 Hz</td>
  </tr>
  <tr>
    <td class="tg-c3ow">5</td>
    <td class="tg-c3ow">Camera 2</td>
    <td class="tg-c3ow">uEye 1221 LE<br>(monochome)</td>
    <td class="tg-0pky">/right/image_raw</td>
    <td class="tg-0pky">sensor_msgs/Image</td>
    <td class="tg-c3ow">10 Hz</td>
  </tr>
  <tr>
    <td class="tg-c3ow" rowspan="3">6</td>
    <td class="tg-c3ow" rowspan="3">UWB</td>
    <td class="tg-c3ow" rowspan="3">Humatic P440</td>
    <td class="tg-0pky">/uwb_endorange_info</td>
    <td class="tg-0pky">uwb_driver/UwbRange</td>
    <td class="tg-c3ow">68.571 Hz</td>
  </tr>
  <tr>
    <td class="tg-0pky">/uwb_exorange_info</td>
    <td class="tg-0pky">uwb_driver/UwbEcho</td>
    <td class="tg-c3ow">5.714 Hz</td>
  </tr>
  <tr>
    <td class="tg-0pky">/node_pos_sc</td>
    <td class="tg-0pky">nav_msgs/Path</td>
    <td class="tg-c3ow">5.714 Hz</td>
  </tr>
  <tr>
    <td class="tg-c3ow">7</td>
    <td class="tg-c3ow">3D Laser Tracker</td>
    <td class="tg-c3ow">Leica MS60<br>TotalStation</td>
    <td class="tg-0pky">/leica/pose/relative</td>
    <td class="tg-0pky">geometry_msgs/PoseStamped</td>
    <td class="tg-c3ow">20 Hz</td>
  </tr>
</tbody>
</table>

## MultiSensors Platform

The IMU being used here is a 9-DoF inertia sensor. The frame of reference attached to this sensor is considered the _body frame_ of the whole setup.

<p align="center">
    <img src="./images/vn100.jpg" alt="Hardware Setup" width="30%"/>
</p>
<p style="text-align: center;">Fig 2. The IMU frame of reference </p> <a name="fig-hardware"></a>

Internally, a filter fuses gyroscope, acceleration, and magnetic field measurements and outputs the orientation result on the `/imu/imu` topic. Though our dataset does not have orientation groundtruth, user can consider this orientation estimate as one.

## Ground Truth
The two cameras are externally triggered to capture images at the same time. For images triggered at the same time, their time stamps are different by **at most 3 ms**. This satisfies the default hardcoded threshold in VINS-Fusion. See our tutorial on how to run VINS-Fusion with the dataset [here]().
