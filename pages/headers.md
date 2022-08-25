---
layout: page-fullwidth
#subheadline: "Header"
title: "Sensor Calibration"
#teaser: "These are your options to style the header of each webpage individually. <em>Feeling Responsive</em> uses <a href='http://srobbin.com/jquery-plugins/backstretch/'>Backstretch by Scott Robin</a> to expand them from left to right. The width should be 1600 pixel or higher using a ratio like 16:9 or 21:9 or 2:1."
header:
   image_fullwidth: "biaoding.jpg"
permalink: "/headers/"
---

## Time Synchronization
<table><tr>
<td width="15%">
Look at this part<br><br><br><br><br><br><br><br>
Look at that part
</td>

<td width="70%">
<p align="left">
    <img src="../images/Time_system.png" alt="Time Sync System" width="100%"/>
</p>
</td>

<td width="15%">
Look at this part<br><br><br><br><br><br><br><br>
Look at that part
</td>
</tr></table>

## IMU
This part is about how we get IMU's gyroscope and accelerometer noise model parameters.

<td><img src="../images/IMU_neican_list.png" width="55%"/></td>

There are three IMUs in the system. First is 9DoF IMU Xsens MTi-G-710 INS/IMU, this is the main IMU of the system with the body frame attached on it. Second is the IMU in LiVOX Lidar which is a 6DoF IMU and well calibrated with LiVOX Lidar. Third is the IMU in ZED 2i stereo camera.

**Take the calibration of Xsens MTi-G-710 as an example:**

**step 1. Record Data**
<table><tr>
<td width="40%"><img src="../images/IMU_neican_calib.png" alt="IMU calib" width="50%"/></td>
<td width="60%">Place the IMU stationary on a stable platform for about 4hours and record the data of IMU in a rosbag.<br><br><br>Downlaod the rosbag file here:<br> <a href="https://rec.ustc.edu.cn/share/11af0a00-d284-11ec-b08d-51a354217a0f">https://rec.ustc.edu.cn/share/11af0a00-d284-11ec-b08d-51a354217a0f</a> <br>
<br>Downlaod the .mat data here:<br> <a href="https://rec.ustc.edu.cn/share/49f8f610-d28b-11ec-8fe1-07b3e2f7cce1">https://rec.ustc.edu.cn/share/49f8f610-d28b-11ec-8fe1-07b3e2f7cce1</a>
</td>
</tr></table>

**step 2. Calibrate**

The tools we use on our calibration are <a href="https://github.com/gaowenliang/imu_utils">imu_utils</a> and <a href="https://github.com/rpng/kalibr_allan">kalibr_allan</a>.
The topic 
{% highlight html %}
> Age is an issue of mind over matter. If you don't mind, it doesn't matter.
<cite>Mark Twain</cite>
<small markdown="1">[Up to table of contents](#toc)</small>
{: .text-right }
{% endhighlight %}

**step 3. Get the Result**
## Camera-IMU
There are 
### 1.Transformation
We use <a href="https://github.com/search?q=Kalibr">Kalibr</a> to calib IMU and Cameras. 
<table><tr>
<td width="45%"><p align="left"><img src="../images/VIO_system_middle.png" width="60%"></p></td>
<td width="25%"><p align="middle"><img src="../images/april_6x6.png" border=0 width="90%"></p></td>
<td width="30%"><p align="right"><img src="../images/Kalibr_ic_error.png" alt="" width="100%"/></p></td>
</tr></table>

### 2.Time estimate
<table><tr>
<td width="60%"><img src="../images/VIO_time_trigger.png" width="100%"></td>
<td>The IMU sensor is synced by PPS signal(1Hz Yellow).<br><br> IMU sync_out trigger line output the trigger signal of camera(20Hz Blue). </td>
</tr></table>

## Velodyne-IMU
### 1.Time Sync

## LiVOX-IMU
### 1.Time Sync

## Mono Cameras
There are 8 mono cameras in the system:<br>
Bumblebee_xb3 left/center/right<br>
Bumbelbee_xb2 left/right<br>
Hikvision_1<br>
Hikvision_2 <br>

## Stereo Cameras

<a href="https://github.com/yzrobot/bumblebee_xb3/wiki/Stereo-vision-bumblebee-xb3-by-anshulpaigwar">Bumblebee_xb3 link</a>

## Velodyne-Cameras
### 1.Time sync

## LiVOX-Camera