---
layout: post
title: 无人驾驶汽车是如何工作的
categories:
- Self-Driving, 
tags:
- Self-Driving, Autonomous, LIDAR, Radar 
---


无人驾驶汽车已经来到我们面前，Uber在匹兹堡和旧金山已经组建了车队，谷歌的母公司正在开展的无人驾驶汽车项目表现出接近量产的信号，联邦政府开始发布无人驾驶汽车将如何工作的指南。本文简要介绍无人驾驶汽车是如何工作的。

## 什么是无人驾驶汽车
无人驾驶汽车是一种能够感知其环境和无需人工输入的导航的车辆。无人驾驶汽车可以使用各种技术（例如雷达，激光雷达，GPS，里程计和计算机视觉）来检测周围环境。 主计算机解释感觉信息，以识别适当的导航路径，以及障碍物和相关标志。

## 无人驾驶汽车是如何工作的

![](/media/pic2017/drive_car.jpg)
原图来自于：Guilbert Gates |Source: Google 
翻译：无人驾驶SelfDriving

### 激光雷达
激光雷达用于构建三维地图，并允许汽车通过从车辆周围的表面发射激光束来发现潜在的危险，以便精确地确定该物体的距离和轮廓。Google汽车使用Velodyne 64光束激光器，通过将激光雷达装置安装到车顶（为了无障碍观看），并允许其在定制的车上选择，为车载处理器提供360度的视角。

### 雷达
尽管激光雷达具有精确映射环境的优点，但是它的一个致命缺点是实时监测周围车辆的速度的能力。4个安装在保险杠上的雷达弥补了这样的缺陷。前保险杠有两个传感器，两个在后保险杠。雷达允许汽车通过向车载处理器发送信号以施加制动或在适当时刻移除车道线来避免撞击。该技术与汽车上的其他功能（例如惯性测量单元，陀螺仪和车轮编码器）结合来向车辆的主计算机发送准确的信号，以便主计算机能够做出更好的决定从而避免潜在的事故。

### 摄像机
每辆无人驾驶汽车上的实际摄像头技术和设置各不相同，但是某些原型汽车使用安装在外边的摄像头，它们稍微分开，以便提供汽车周围的重叠视图。这种技术与人眼不同，人眼在确定诸如景深，周边运动和目标的维度之类的事物之前向大脑提供重叠的图像。

### 定位
如果没有高级定位系统来跟踪其路径，并绘制其到目的地的适当路线，那没有方向盘，没有制动器和没有加速器的汽车将基本是无用的。对于这一挑战，google使用自己的地图系统以及GPS卫星，惯性测量单元和轮式编码器来确定实际速度。该系统与车载相机，GPS数据和驾驶速度一起处理真实世界信息，以便于准确地确定每辆车的精确位置（精度可达几厘米），对交通、道路建设和事故等事情进行智能修正。

### 复杂的软件
该软件实时处理所有数据，以及其他驾驶员、行人和周围物体的动态模型。虽然一些数据被硬编码到汽车中，例如在红灯处停止。但是其他的反应需要给予以前的经验来学习。每辆车的每一英里数据都被记录。这些数据将被处理以便去找到每种情况都适用的解决方案。
学习算法不仅处理你驾驶的车的数据，而且处理其他车的数据，以找到对每一个可能问题的适当响应。行为学也会被映射，并且这些数据用于帮助在事件发生前进行预判，这一点非常像人类驾驶员。例如，汽车非常聪明，足以识别和适应以下场景：
如果一辆车在右侧缓慢行驶，那么跟在他后面的车有很大的概率会超车；
如果街道上有坑洞，那么驾驶员有很大的概率会转向以避开他；
如果左侧车道拥堵，意味着驾驶员有很大概率会向右并线。

## 你可能已经使用的自动驾驶功能
### 碰撞回避
基于雷达，激光或者相机的系统，告警即将发生的碰撞。系统识别行人闯入行进路线，如果司机忽略警告，有些系统将采取制动。  
![](/media/pic2017/1-collision.jpg)

### 车道偏离报警
当你的汽车开始偏离行车线时候，系统会通过蜂鸣器来向驾驶员告警，并且增加轻微的反向力作用到方向盘。  
 ![](/media/pic2017/2-drifting.jpg)

### 盲区检测
使用摄像机或雷达检测驾驶员盲区的车辆。通过声音，或者汽车挡风玻璃旁的的支柱或后视镜上警告灯来向驾驶员告警。  
![](/media/pic2017/3-blind.jpg)

### 自动跟车控制
与前方车辆保持预定车距。如果它减慢，你的车也减慢。如果一辆车进入你的车道，你的车仍然保持车距。这样功能在堵车时候有用。  
 ![](/media/pic2017/4-cruise.jpg)

### 自助泊车
汽车使用相机或声纳将自身调整到停车位。 但是司机通常必须制动和跟随命令。 它首次出现在2003年在丰田普锐斯。 宝马，福特和许多其他车上也有了类似功能。  
 ![](/media/pic2017/5-parking.jpg)