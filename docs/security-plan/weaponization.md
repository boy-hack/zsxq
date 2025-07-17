# 安全补全计划 - 武器化开发篇

本篇章专注于将安全技术转化为实用的工具和武器，内容涵盖红队开发的多个方面。

## 📚 知识点列表

1.  **微信聊天记录解密**
    -   研究PC端微信的数据加密和存储机制，实现对聊天记录的解密。
    -   [通用的内存微信获取个人信息方式](https://t.zsxq.com/QbIy7UZ)
        -   通过定位到微信内部的数据结构获取微信个人信息，不需要每个版本定位内存偏移。

2.  **文件系统分析平台**
    -   学习如何构建一个类似Everything的快速文件检索引擎。
    -   [everything导出数据](https://t.zsxq.com/05ubIq3na)

3.  **DLL劫持与白加黑自动化改造**
    -   深入研究DLL劫持的原理和利用技巧，并学习如何将其自动化。
    -   系列文章:
        -   [DLL劫持研究 (一)](https://t.zsxq.com/ZRZRbUB)
        -   [DLL劫持研究 (二)](https://t.zsxq.com/Ju7aMzf)
        -   [DLL劫持研究 (三)](https://t.zsxq.com/EeiieY7)
        -   [DLL劫持研究 (四)](https://t.zsxq.com/Qv3BUny)
        -   [DLL劫持研究 (五)](https://t.zsxq.com/NfAaQje)
        -   [DLL劫持研究 (六)](https://t.zsxq.com/QZjY76Y)
        -   [DLL劫持研究 (七)](https://t.zsxq.com/v3RRrrz)
        -   [DLL劫持研究 (八)](https://t.zsxq.com/rNrBA6m)

4.  **DLL自动化劫持**
    -   编写工具，自动分析目标程序并生成可用的代理DLL。
    -   [100行代码实现通用劫持dll](https://t.zsxq.com/05ZrjEiEe)
    -   [代理DLL自动生成，构建转发导出表(Go源码)](https://t.zsxq.com/05aYByVFy)

5.  **资产扫描管理系统**
    -   设计和开发一个用于管理和扫描大规模资产的系统。

6.  **RAT (Remote Access Trojan)**
    -   学习远控木马的设计和实现，包括C2通信、任务执行等。
    -   [Go Rat + electron](https://t.zsxq.com/JE27iea)
    -   [BIOPASS RAT 源码](https://t.zsxq.com/qR3nmuV)
    -   [xss spoof欺骗模块](https://t.zsxq.com/jmUZVVb)

7.  **内存马**
    -   研究在Web应用中植入无文件后门的技术，构建内存马生成框架。
    -   [内存马生成框架](https://t.zsxq.com/05nEqB6uv) 