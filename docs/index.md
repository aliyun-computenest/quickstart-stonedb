# Demo服务实例部署文档
## 概述
TuGraph（tugraph.org）是蚂蚁集团的高性能图数据库（Graph Database）及图数据管理平台。TuGraph在计算巢上提供了社区版服务，您无需自行配置云主机，即可在计算巢上快速部署TuGraph服务、实现运维监控，从而方便地基于TuGraph搭建您自己的图应用。本文向您介绍如何开通计算巢上的TuGraph社区版服务，以及部署流程和使用说明。
## 计费说明
TuGraph社区版在计算巢上的费用主要涉及：

- 所选vCPU与内存规格
- 系统盘类型及容量
- 公网带宽

计费方式包括：

- 按量付费（小时）
- 包年包月

目前提供如下实例：

| 规格族 | vCPU与内存 | 系统盘 | 公网带宽 |
| --- | --- | --- | --- |
| ecs.r6.xlarge | 内存型r6，4vCPU 32GiB | ESSD云盘 200GiB PL0 | 固定带宽1Mbps |

预估费用在创建实例时可实时看到。
如需更多规格、其他服务（如集群高可用性要求、企业级支持服务等），请联系我们 [tugraph@service.alipay.com](mailto:tugraph@service.alipay.com)。
## 
## 部署架构
TuGraph社区版采用单机部署的架构，存储计算以及web服务都在一个台服务器上。

## RAM账号所需权限
TuGraph服务需要对ECS、VPC等资源进行访问和创建操作，若您使用RAM用户创建服务实例，需要在创建服务实例前，对使用的RAM用户的账号添加相应资源的权限。添加RAM权限的详细操作，请参见[为RAM用户授权](https://help.aliyun.com/document_detail/121945.html)。所需权限如下表所示。

| 权限策略名称 | 备注 |
| --- | --- |
| AliyunECSFullAccess | 管理云服务器服务（ECS）的权限 |
| AliyunVPCFullAccess | 管理专有网络（VPC）的权限 |
| AliyunROSFullAccess | 管理资源编排服务（ROS）的权限 |
| AliyunComputeNestUserFullAccess | 管理计算巢服务（ComputeNest）的用户侧权限 |
| AliyunCloudMonitorFullAccess | 管理云监控（CloudMonitor）的权限 |


## 部署流程
### 部署步骤

1. 单击下面的部署链接，进入服务实例部署界面，根据界面提示，填写参数完成部署。

[部署链接](https://computenest.console.aliyun.com/user/cn-hangzhou/serviceInstanceCreate?spm=5176.24779694.0.0.3d9d4d22Kr7osZ&ServiceId=service-7b50ea3d20e643da95bf)

1. 单击部署链接。在创建服务实例页面，需先选中 **同意授权并创建关联角色** ，选中后即可继续创建服务实例。

![1.png](1.png)
### 
### 部署参数说明
您在创建服务实例的过程中，需要配置服务实例信息。下文介绍云XR实时渲染平台服务实例输入参数的详细信息。

| 参数组 | 参数项 | 示例 | 说明 |
| --- | --- | --- | --- |
| 服务实例名称 |  | test | 实例的名称 |
| 地域 |  | 华北2（北京） | 选中服务实例的地域，建议就近选中，以获取更好的网络延时。 |
| 付费类型配置 | 付费类型 | 按量付费 或 包年包月 | 
 |
| 可用区配置 | 部署区域 | 可用区I | 地域下的不同可用区域 |
| 选择已有基础资源配置 | VPC ID | vpc-xxx | 选择专有网络的ID。 |
| 选择已有基础资源配置 | 交换机ID | vsw-xxx | 选择交换机ID。若找不到交换机, 可尝试切换地域和可用区 |
| ECS实例配置 | 实例类型 | ecs.r6.xlarge | 当前仅支持ecs.r6.xlarge规格 |
| ECS实例配置 | 实例密码 | ******** | 设置实例密码。长度8~30个字符，必须包含三项（大写字母、小写字母、数字、 ()`~!@#$%^&*_-+={}[]:;'<>,.?/ 中的特殊符号）。 |

![2.png](2.png)

### 
### 验证结果

1. 查看服务实例。
服务实例创建成功后，部署时间大约需要2分钟。部署完成后，页面上可以看到对应的服务实例。 

![3.png](3.png)

2. 通过服务实例访问TuGraph

![4.png](4.png)
进入到对应的服务实例后，可以在页面上获取到web、rpc、ssh共3种使用方式。


### 使用TuGraph
请访问TuGraph官网了解如何使用TuGraph：[TuGraph可视化使用文档](https://www.tugraph.org/doc?version=V3.3.0&id=10000000001031969)

## 问题排查
请访问TuGraph-db on Github的[Discussion](https://github.com/TuGraph-db/tugraph-db/discussions/115)获取帮助

## 联系我们
欢迎访问TuGraph官网（[https://www.tugraph.org/](https://www.tugraph.org/)）了解更多信息。
联系邮箱：[tugraph@service.alipay.com](mailto:tugraph@service.alipay.com)
社区版开源地址：[https://github.com/TuGraph-db/tugraph-db](https://github.com/TuGraph-db/tugraph-db)
扫码关注微信公众号，技术博客、活动通知不容错过：

![%.png](5.png)
