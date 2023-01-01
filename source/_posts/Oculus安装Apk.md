---
title: Oculus安装Apk
date: 2023-01-01 16:56:14
tags:
---


- 确保PC能使用`adb`命令
- 将`Oculus`连接`PC`并开机
- 在`something.apk`所在的文件夹空白处，按住`shift`，鼠标`右键`，选择`在此处打开PowerShell窗口`
- 等待`PowerShell`窗口初始化完成，输入命令，`adb devices`，回车，确保输出中有`Oculus`设备
- 输入`adb install something.apk`，等待安装完成即可