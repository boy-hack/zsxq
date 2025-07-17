# 安全补全计划 - 自动化扫描篇

本篇章专注于自动化扫描技术的各个方面，从基础的HTTP请求到高级的扫描器开发。

## 📚 知识点列表

1.  **http(s) 请求**
    -   深入理解HTTP/HTTPS协议，掌握如何构造和解析HTTP报文。
2.  **指纹识别**
    -   学习各种Web指纹识别技术，包括基于关键字、Header、ICO等。
    -   [Goby指纹的提取和YARA逆向](https://t.zsxq.com/q7E2Nfe)
    -   [Golang版的TideFinger](https://t.zsxq.com/05AEU7yB6)
3.  **子域名与爆破**
    -   掌握各种子域名发现技术，并学习如何编写高效的爆破工具。
    -   [ksubdomain新版发布，github action 自动编译三平台](https://t.zsxq.com/uzjAQbu)
4.  **端口扫描**
    -   学习TCP/UDP端口扫描原理，实现类似Nmap的端口扫描和服务识别功能。
    -   [像fofa一样解析RDP信息](https://t.zsxq.com/09nOE6IIC)
    -   [golang实现nmap os detection](https://t.zsxq.com/09qFwd3x6)
5.  **PoC验证与集成**
    -   学习如何编写标准化的PoC，并构建一个兼容多种格式（如xray, nuclei）的验证框架。
    -   [w14scan 更新啦，开放源码！ 完成了第三期作业 《兼容xray和nuclei的poc验证工具》](https://t.zsxq.com/27UJm2v)
    -   [woodpecker](https://t.zsxq.com/05By33bae)
6.  **扫描规则**
    -   学习编写高效的扫描规则，用于发现特定漏洞。
    -   [域传送批量检测 Go源码](https://t.zsxq.com/022RV7e6U)
    -   [log4j被动检测](https://t.zsxq.com/053ZnUJqv)
7.  **XSS扫描器**
    -   深入研究XSS漏洞的原理和利用方式，从零开始构建一个自动化的XSS扫描器。
    -   **xscan扫描器**: 输入url自动化爬虫+XSS扫描，bugbounty挖洞神器
        -   [xscan v1.4 更新发布](https://t.zsxq.com/0bcRm0Sp4)
        -   [xscan 更新 v1.2](https://t.zsxq.com/02au3FMFM)
        -   [xscan v0.8](https://t.zsxq.com/02MBaAiqv)
        -   [xscan v0.1 发布](https://t.zsxq.com/02uz7iuzr)
    -   **dom-xss-scan**: 开源的DOM XSS检测工具
        -   [dom-xss-scan 开源](https://t.zsxq.com/0dD7RF9YW)
8.  **爬虫**
    -   学习Web爬虫技术，特别是能够处理JavaScript动态渲染页面的动态爬虫。
    -   **crawlergo源码的学习**:
        -   [crawlergo源码的学习，以前就想写动态爬虫了，因为能原生干很多事情，现在终于可以试试了.准备写一份更新在知识星球 (又开一坑)](https://t.zsxq.com/JIYNNNR)
        -   [动态爬虫学习(二)](https://t.zsxq.com/JYbuBEQ)
        -   [动态爬虫学习(三)](https://t.zsxq.com/6MNfauz)
9.  **bugbounty**
    -   分享自动化BugBounty的经验和流程。
    -   [我自动化获得微软漏洞赏金的经历](https://t.zsxq.com/a6Aie2f)
    -   [我的xss bugbounty自动化步骤](https://t.zsxq.com/05jIqrnEu)
10. **其他**
    -   探讨扫描中遇到的一些通用问题和算法。
    -   [计算最短CIDR](https://t.zsxq.com/05au3bieQ)
    -   [随机化扫描算法Go实现](https://t.zsxq.com/09JHV6FTA)
    -   [一个Go协程可取消的并发模型](https://t.zsxq.com/09YztbRVD)
    -   [资产收集之spf记录](https://t.zsxq.com/09JC1feZW)
    -   [退避重试算法](https://t.zsxq.com/0baRkmawG)
    -   [web扫描中重定向问题](https://t.zsxq.com/0b1ewVIjN) 