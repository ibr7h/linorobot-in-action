# Linorobot in Action

Build a linorobot from scratch

> This is a document project describe how to build a [linorobot](https://github.com/linorobot/linorobot) from scratch.

## Table of content
* [Introduction](https://github.com/jacks808/linorobot-in-action/tree/master#introduction)
* [Hardware](https://github.com/jacks808/linorobot-in-action/tree/master#hardware)
* [Hardware test and driver installation](https://github.com/jacks808/linorobot-in-action#hardware-test-and-driver-installation)
* [Software](https://github.com/jacks808/linorobot-in-action/tree/master#software)
* Debug&test
* FAQ
* Update Notes
* [Useful links](https://github.com/jacks808/linorobot-in-action/tree/master#useful-links)

## Introduction

This github project is describe how to build a Linorobot from scratch. Includeing hardware, software, debug and test.

Linorobot is a suite of Open Source ROS compatible robots that aims to provide students, developers, 
and researchers a low-cost platform in creating new exciting applications on top of ROS. More about Linorobot can be found 
[here](https://github.com/linorobot/linorobot)

Author of this project: jack.wang a fullstack engneree focus on software, robots and autonomous vehicle.

## Hardware

In this part, I will tell how to build hardware part about linorobot. Including Hardware  and how to assemble them together. 

### Hardware list

Here is the hardware list that I used, all of this part can be found at [Taobao](www.taobao.com) or [Amazon](www.amazon.com)

* Laser sensors: 

  [RPLIDAR-A1 @Taobao](https://item.taobao.com/item.htm?spm=a1z09.2.0.0.56142e8dDnARXB&id=562109534912&_u=7cvg7t6a007)

  [RPLiDAR-X4 @Amazon](https://www.amazon.com/YDLIDAR-X4-Lidar-Rangefinder-Scanner/dp/B078Y964ZS/ref=sr_1_1?ie=UTF8&qid=1538989975&sr=8-1&keywords=rplidar+a1)

* IMU:

  [GY-85 @Taobao](https://item.taobao.com/item.htm?spm=a1z09.2.0.0.56142e8dDnARXB&id=17523968036&_u=7cvg7t6d225)

  [GY-85 @Amazon](https://www.amazon.com/KNACRO-Modules-Accelerometer-Gyroscope-HMC5883L/dp/B06WWF2F5R/ref=sr_1_1?ie=UTF8&qid=1538990050&sr=8-1&keywords=GY-85)

* Micro-controller:

  [Teensy 3.6 @Taobao](https://detail.tmall.com/item.htm?id=563186976177&spm=a1z09.2.0.0.56142e8dDnARXB&_u=7cvg7t6e88f)

  [Teensy 3.6 @Amazon](https://www.amazon.com/PJRC-Teensy-3-6-M4-Cortex/dp/B0778TTG1H/ref=sr_1_3?ie=UTF8&qid=1538990179&sr=8-3&keywords=Teensy+3.6)

* Ubuntu install ARM based dev board:

  [Raspberry Pi 3/B+ @Taobao](https://item.taobao.com/item.htm?spm=a230r.1.14.20.784f7790h9SvRU&id=550270480898&ns=1&abbucket=14#detail)

  [Raspberry Pi 3/B+ @Amazon](https://www.amazon.com/CanaKit-Raspberry-Starter-Premium-Black/dp/B07BCC8PK7/ref=sr_1_1_sspa?s=pc&ie=UTF8&qid=1538990222&sr=1-1-spons&keywords=raspberry+pi+3+b%2B&psc=1)

* Motor Drivers:

  [BTS7960 @Taobao](https://item.taobao.com/item.htm?spm=a1z09.2.0.0.56142e8dDnARXB&id=523962217259&_u=7cvg7t6d20d)

  [BTS7960 @Amazon](https://www.amazon.com/MonkeyJack-Double-BTS7960-H-bridge-Stepper/dp/B076CQBXHM/ref=sr_1_2?s=electronics&ie=UTF8&qid=1538990308&sr=1-2&keywords=BTS7960)

* Motor and Wheels:

  [Homemade chassis @Taobao](https://item.taobao.com/item.htm?spm=a1z09.2.0.0.56142e8dDnARXB&id=569175144674&_u=7cvg7t6dbb4)

  [Homemade chassis @Amazon](https://www.amazon.com/dp/B009646R3K/ref=sspa_dk_detail_5?psc=1&pd_rd_i=B009646R3K&pf_rd_m=ATVPDKIKX0DER&pf_rd_p=f52e26da-1287-4616-824b-efc564ff75a4&pf_rd_r=Y4R2S83Z4MM9ETJ2T364&pd_rd_wg=7fjFE&pf_rd_s=desktop-dp-sims&pf_rd_t=40701&pd_rd_w=jZtYv&pf_rd_i=desktop-dp-sims&pd_rd_r=42488e80-cadb-11e8-8f13-cb169b2924c1)

* connecting wires:

  [Dupont Line @Taobao](https://detail.tmall.com/item.htm?id=17525560371&spm=a1z09.2.0.0.56142e8dDnARXB&_u=7cvg7t6db4b&skuId=3110508296812)

  [Dupont Line @Amazon](https://www.amazon.com/Willwin-Dupont-80pcs-female-jumper/dp/B07566DGHZ/ref=sr_1_2_sspa?s=industrial&ie=UTF8&qid=1538990424&sr=1-2-spons&keywords=Dupont+Line&psc=1)

More supported hardware can be found [here](https://github.com/linorobot/linorobot/wiki/1.-Getting-Started#11-what-you-need)

### Assemble

// Todo

## Hardware test and driver installation

In this section, I will show you how to make sure hardware works well, and install the required drivers. 

### Laser sensor



![https://www.slamtec.com/en/Lidar/A1Spec](https://ws2.sinaimg.cn/large/006tNbRwly1fw395sempej30bh07hdg9.jpg)

<div align=center><a href="https://www.slamtec.com/en/Lidar/A1">PRLiDar A1</a></div>

> `RPLIDAR A1` contains a range scanner system and a motor system. After power on
> each sub-system, `RPLIDAR A1` start rotating and scanning clockwise. User can get
> range scan data through the communication interface (Serial port/USB).
>
> Reference from [RPLiDAR datasheet](http://bucket.download.slamtec.com/8e7a1f4490a235717b43fccaf7dcae325dda7dc8/LD108_SLAMTEC_rplidar_datasheet_A1M8_v2.1_en.pdf)

#### Hardware test

1. Assemble `PRLiDAR A1`  with drive board .

2. Find a `Micro USB-B` ![image-20181010174342181](https://ws3.sinaimg.cn/large/006tNbRwly1fw39pevz9wj302f02b3ye.jpg) Line, connect drive board to your computer

3. Then LiDAR should start rotating clockwise.

   <div align=center><img src="https://ws3.sinaimg.cn/large/006tNbRwly1fw39wrwagwj30c60em40v.jpg"></div>

#### Driver installation (MacOS)

1. Install serial port driver

   Driver installation file can be found at [CP210x USB to UART Bridge VCP Drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)

2. Download SDK from github

   ```bash
   git clone git@github.com:Slamtec/rplidar_sdk.git
   ```

3. Complie SDK

   Make sure you have `g++` installed and run: 

   ```bash
   cd rplidar_sdk_v1.9.0_1/sdk && make
   ```

   After compile, directory `output/Darwin/Release` should be generated. And you can find: 

   * simple_grabber 

     This demo application simply connects to an RPLIDAR device and outputs the scan data to the console.

   * ultra_simple

     This demo application grabs two round of scan data and shows the range data as histogram in the command line mode.

4. Find USB serial:

   ```bash
   ls -l /dev/tty.*
   ```

   If you see `/dev/tty.SLAB_USBtoUART` That means driver is work:

   ![image-20181010180503117](https://ws2.sinaimg.cn/large/006tNbRwly1fw3abl7agwj30k6030wf8.jpg)

5. Run `simple_grabber`

   In directory: `rplidar_sdk_v1.9.0_1/sdk/output/Darwin/Release`

   ```bash
   ./ultra_simple /dev/tty.SLAB_USBtoUART
   ```

   You should see something like this:

   ```
   Ultra simple LIDAR data grabber for RPLIDAR.
   Version: 1.9.0
   RPLIDAR S/N: 52989AF0C5E29DD2B6E39DF5D14B3116
   Firmware Ver: 1.24
   Hardware Rev: 5
   RPLidar health status : 0
   *WARN* YOU ARE USING DEPRECATED API: grabScanData(), PLEASE MOVE TO grabScanDataHq()
   *WARN* YOU ARE USING DEPRECATED API: ascendScanData(rplidar_response_measurement_node_t*, size_t), PLEASE MOVE TO ascendScanData(rplidar_response_measurement_node_hq_t*, size_t)
      theta: 0.55 Dist: 00898.00 Q: 47
      theta: 1.59 Dist: 00000.00 Q: 0
      theta: 2.14 Dist: 00000.00 Q: 0
      theta: 2.67 Dist: 00000.00 Q: 0
      theta: 3.22 Dist: 00000.00 Q: 0
      theta: 3.75 Dist: 00000.00 Q: 0
      theta: 4.30 Dist: 00000.00 Q: 0
      theta: 4.83 Dist: 00000.00 Q: 0
      theta: 7.00 Dist: 00000.00 Q: 0
      theta: 7.53 Dist: 00000.00 Q: 0
      theta: 8.08 Dist: 00000.00 Q: 0
      theta: 8.61 Dist: 00000.00 Q: 0
      theta: 9.16 Dist: 00000.00 Q: 0
      theta: 9.69 Dist: 00000.00 Q: 0
      theta: 10.23 Dist: 00000.00 Q: 0
      theta: 10.77 Dist: 00000.00 Q: 0
   ```

## Software

In this part, I will introduce how to install ROS on Respberry Pi. After that, linorobot Installation will be shown step by step. 

### Install OS for Raspberry Pi

![This image is comes from [here](https://ws3.sinaimg.cn/large/006tNbRwly1fw124ed5m7g30j40a1dj1.gif)](https://www.raspberrypi.org/app/uploads/2018/07/42558525-6dd32c62-84e9-11e8-99d2-0281ffe300c3.gif)

Usually, I use Ubuntu 16.04 for ROS, but after read this document: [Installing ROS Kinetic on the Raspberry Pi](http://wiki.ros.org/ROSberryPi/Installing%20ROS%20Kinetic%20on%20the%20Raspberry%20Pi). I directly install pre-installed Ros Ubuntu image offer by `Ubiquity`, which can be found [here](https://downloads.ubiquityrobotics.com/pi.html). 

Install steps:

1. Download `img` file for Respberry Pi: [Img Link](https://cdn.ubiquityrobotics.net/2018-06-27-ubiquity-xenial-lxde-raspberry-pi.img.xz)

2. Use [`Etcher`](https://etcher.io/) to write `image` to Respberry Pi SD card:

   1. Select Image

   2. Select Drive

   3. Flash

   4. Validating

      If everything is OK, you should see this:

      ![Jietu20181008-171027@2x](https://ws2.sinaimg.cn/large/006tNbRwly1fw11qz7er4j318g0l477n.jpg)

3. Insert in your TF card to Respberry Pi. Power on, And wait some time (in 3 mins)
4. Open Wifi config page to find a new Wifi point named: `ubiquityrobotXXXX` where XXXX is part of the MAC address. The wifi password is `robotseverywhere`.
5. After connected, use `ssh ubuntu@10.42.0.1` with a password `ubuntu` to login.

If everything is OK you should see this:

![image-20181008194204967](https://ws1.sinaimg.cn/large/006tNbRwly1fw11w6lxc2j30j60emmzz.jpg)

And ros is installed:

![image-20181008195309767](https://ws4.sinaimg.cn/large/006tNbRwly1fw127g9kj1j30hz09ywfz.jpg)



### Make your Respberry Pi connect to internet

To install needed software, we need to make Respberry Pi connect to internet. 

On Mac OS, use `share network`  to share a internet connection to Respberry Pi is very simple. Here is the way:

1. Connect Mac to a AP with internet. (Note: Please Do NOT use `802.1x` wifi AP)

2. Connect Respberry Pi to Mac with a network line. 

3. Open `System Settings`-> `Share `: ![image-20181012202422842](https://ws3.sinaimg.cn/large/006tNbRwly1fw5pl7i763j302g020dfv.jpg) , and config like show bellow: 

   ![image-20181012202610951](https://ws3.sinaimg.cn/large/006tNbRwly1fw5pn1pjxwj31140tigs4.jpg)

4. Open a terminal, run: `arp -a` to find all host on same AP, find the host marked as  `bridge`

   ![image-20181012203237843](https://ws1.sinaimg.cn/large/006tNbRwly1fw5ptriebxj30io09faj6.jpg)

5. `ssh ubuntu@192.169.2.2` 

6. Test network status:  `ping baidu.com`

   ![image-20181012203603659](https://ws2.sinaimg.cn/large/006tNbRwly1fw5pxblryaj30fi03f0vu.jpg)

If everything is OK, your Respberry Pi will connect to internet. 

### Linorobot Installation

In this section, I will show how to install linorobot on Respberry Pi. 

1. Login in to your Respberry Pi: 

   `ssh ubuntu@192.168.2.2`

2. clone the install package:

   ```bash
   git clone https://github.com/linorobot/lino_install
   cd lino_install
   ```

3. For Raspberry Pis it is recommended to have a swap file to prevent the initial build from failing. You can disable this once the installation is done.

   ```bash
   sudo apt-get install dphys-swapfile
   ```

4. Run install script, where base in( `2wd`, `4wd`, `ackermann`, `mecanum`) and sensor in( `xv11`, `rplidar`, `ydlidar`, `hokuyo`, `kinect`, `realsense`). I am use `2wd` base and `rplidar`, so run: 

5. ```
   ./install 2wd rplidar
   ```

   Then, you will see this:

   ```bash
   armv7l
   
   ______ _____________   _________ ________ _______ ________ _______  
   ___  / ____  _/___  | / /__  __ \___  __ \__  __ \___  __ )__  __ \___  
   __  /   __  /  __   |/ / _  / / /__  /_/ /_  / / /__  __  |_  / / /__  /
   _  /_____/ /   _  /|  /  / /_/ / _  _, _/ / /_/ / _  /_/ / / /_/ / _  /
   /_____//___/   /_/ |_/   \____/  /_/ |_|  \____/  /_____/  \____/  /_/
   
                               http://linorobot.org
   
   
   You are installing ROS-kinetic Linorobot for 2wd base with a rplidar sensor. Enter [y] to continue.
   ```

   Entry `y` 

6. Wait to finish, (It takes me more than 30 mins, so be patient)

Some issue you maybe face: 

*  `unsupported locale setting `, try [this](https://stackoverflow.com/a/36257050/1547817) 
* `fatal error: lino_msgs/PID.h: No such file or directory`, rerun install script several times. 

## Update Notes

* 2018-10-10 Add `Hardware test and driver installation` include `laser sensor`
* 2018-10-12 Add `Make your Respberry Pi connect to internet` and `Linorobot Installation`

## Useful links

* Linorobot home page: https://linorobot.org
* Linorobot getting stated: https://github.com/linorobot/linorobot/wiki/1.-Getting-Started#11-what-you-need
* Ros home page: http://ros.org
* Respberry Help page: https://www.raspberrypi.org/help/
* Ubiquityrobotics home page: https://ubiquityrobotics.com/
* INTRODUCING THE TEENSY 3.5 AND 3.6: https://hackaday.com/2016/08/17/introducing-the-teensy-3-5-and-3-6/
* PRLiDAR A1 Download page: https://www.slamtec.com/en/Support#rplidar-a1
* PRLiDAR SDK: https://github.com/slamtec/rplidar_sdk
* PRLiDAR ROS: https://github.com/slamtec/rplidar_ros
