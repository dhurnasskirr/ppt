# DMIT VPS 使用全指南：从购买到流量管理的完整教程

DMIT 全新升级的管理后台提供了更直观的 UI 设计，让 VPS 管理变得简单高效。本文将详细介绍购买后的各项管理操作，包括系统重装、root密码设置、密钥管理、流量计费等核心功能。

## 一、流量计费策略详解

DMIT 对部分套餐实施了全新的流量计算方式，采用 **MAX(IN, OUT)** 单向取最大值策略：

- **适用套餐**：HKG.T1、SJC.T1等特定套餐
- **计费特点**：仅统计入站和出站流量中的较大值
- **生效时间**：系统已于8月16日UTC 0点开始实施新统计方式

### 不同套餐的流量规则对比

1. **PVM.HKG.T1.STARTER**  
   - 单向流量计费（取最大值）
   - 超量后自动降速

2. **PVM.LAX.sPro.CREATOR**  
   - 双向流量计费
   - 超量后服务暂停

3. **PVM.HKG.Pro**  
   - 双向流量计费
   - 超量后服务暂停

👉 [【点击查看】2025年最新 DMIT 优惠码及特价云服务器方案汇总](https://bit.ly/dmit_coupon)

## 二、SSH密钥登录与Root密码设置

### 密钥登录基础
- 官方文档参考：https://www.dmit.io/knowledgebase.php
- 支持自定义密钥配置

### Root密码设置教程（Debian11系统）

**重要提示**：
- 默认Root密码仅用于控制台访问
- 修改后需完成电源重启（关机→开机）才能生效
- 如需SSH登录，需额外修改SSH配置

#### 方法一：命令行快速设置
bash
passwd # 设置密码
sudo sed -i 's/^#\?PermitRootLogin.*/PermitRootLogin yes/g' /etc/ssh/sshd_config;
sudo sed -i 's/^#\?PasswordAuthentication.*/PasswordAuthentication yes/g' /etc/ssh/sshd_config;
sudo service sshd restart
reboot # 重启服务器

#### 方法二：手动配置文件修改
bash
sudo -i # 切换root用户（DMIT默认已root登录可省略）
passwd # 设置密码
nano /etc/ssh/sshd_config # 编辑配置文件
# 修改以下参数：
PermitRootLogin yes
PasswordAuthentication yes
reboot # 重启生效

## 三、实用管理功能

### 1. 快照功能
- 提供1个免费快照
- 支持系统状态备份与恢复

### 2. 系统重装
- 支持多种Linux发行版
- 提供纯净系统环境

### 3. 账单管理
- 续费操作简单直观
- 可随时取消自动续费

## 四、洛杉矶PVM.LAX.Pro套餐优势

- **网络线路**：
  - 电信：去程GIA(AS4809)
  - 联通：去程直连AS4837
  - 移动：去程香港移动(AS58453)
- **回程**：三网统一GIA(AS4809)优质线路