# 安全补全计划 - 工具与原理篇

本篇章专注于剖析现有优秀安全工具的实现原理和核心思想，通过学习它们的设计来提升自己的开发能力。

## 📚 知识点列表

1.  **sliver c2相关的原理**
    -   深入分析 Sliver C2 的架构、通信协议和模块化设计。
    -   [sliver c2相关的原理](https://t.zsxq.com/ny7IIUj)

2.  **Windows补丁对比工具是怎么做的？**
    -   学习 Bindiff 等工具的原理，了解如何通过二进制比对来分析补丁修复的漏洞。
    -   [Windows补丁对比工具是怎么做的？](https://t.zsxq.com/6yv7AEi)

3.  **ssrfmap 原理**
    -   剖析 ssrfmap 的工作流程，了解其如何自动化地探测和利用 SSRF 漏洞。
    -   [ssrfmap 原理](https://t.zsxq.com/z7yFIIE)

4.  **dom-based-xss-finder 采用AST+js动态hook查找dom-xss的原理**
    -   研究 dom-based-xss-finder 如何通过AST（抽象语法树）解析和JS动态Hook来精准发现DOM-XSS，并给出调用堆栈。
    -   [dom-based-xss-finder 原理](https://t.zsxq.com/6YfEAeE)

5.  **XssSnpier原理**
    -   分析来自 360 的 Chrome 插件 XssSnpier 的工作原理，它如何基于 Fuzz 和监控 error 报错信息来半自动地检测XSS。
    -   [XssSnpier原理](https://t.zsxq.com/2RbuZ7U)

6.  **dalfox源码学习**
    -   学习基于 Golang 的 XSS 扫描器 dalfox 的源码，重点理解其基于 DOM 解析器的扫描方式。
    -   [dalfox源码学习](https://t.zsxq.com/3rZbi2r)

7.  **CS上线器源码和相关原理**
    -   分析 Cobalt Strike Stager 的工作原理和源码实现。
    -   [CS上线器源码(一)](https://t.zsxq.com/uVnqjyb)
    -   [CS上线器源码(二)](https://t.zsxq.com/jyfAynI)

8.  **对SigFlip(将数据隐写到已签名的PE文件上)的原理探究**
    -   研究 SigFlip 技术如何在不破坏数字签名的情况下，向已签名的PE文件中隐写数据。
    -   [对SigFlip的原理探究](https://t.zsxq.com/EIeqV7y)

9.  **读读fingerprintx，一个端口识别工具**
    -   分析 fingerprintx 的指纹识别原理和实现细节。
    -   [读读fingerprintx](https://t.zsxq.com/09a9GMJZg)

10. **把玩donut**
    -   学习 donut 工具如何将 .NET 程序集转换为 Shellcode。
    -   [把玩donut](https://t.zsxq.com/09YN1UB3i) 