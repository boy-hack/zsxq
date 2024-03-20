# Hacking自动化 安全补全计划
Hacking自动化就是好玩的星球相关

- [点击星球预览](https://public.zsxq.com/groups/15522244414512.html)
- [点击星球介绍](https://mp.weixin.qq.com/s?__biz=MzU2NzcwNTY3Mg==&mid=2247484177&idx=1&sn=e394fc7db94d90fd64b2402ba54a4731&chksm=fc986a36cbefe3202b37f8943b11b98176b14d0f2c139857b5510c2ac49acf2e462d06629799&token=338286590&lang=zh_CN#rd)
- [2023知识星球总结](https://mp.weixin.qq.com/s?__biz=MzU2NzcwNTY3Mg==&mid=2247484972&idx=1&sn=ceb3c486344f03f7278249efcb77889d&chksm=fc986f0bcbefe61da887e0e747217d46c8f3eaba15e7d78f593f4718f1865544ab50b57b4aec&token=1598106325&lang=zh_CN#rd)

> 很多黑客和安全工具的构造是那么巧妙，我看了很多安全工具的代码，将它们值得学习的地方记录了下来。这个仓库将持续更新星球中的精华文章和补全安全知识，记录笔记，对自己对他人都是一种收获。付费加入是我更新的动力。

ps: 随时修改，有链接的是正在补全的知识，无链接的代表占位的知识，等以后补全。

星球购买，每月仅限100名 http://pay.hacking8.xyz/buy/2

- [Hacking自动化 安全补全计划](#hacking自动化-安全补全计划)
  - [星球作业整理](#星球作业整理)
  - [安全补全计划](#安全补全计划)
    - [恶意软件篇](#恶意软件篇)
    - [自动化扫描篇](#自动化扫描篇)
    - [自动化脚本篇](#自动化脚本篇)
    - [漏洞与研究篇](#漏洞与研究篇)
    - [武器化开发篇](#武器化开发篇)
    - [工具与原理篇](#工具与原理篇)
    - [其他想法](#其他想法)


## 星球作业整理
- 第一期：Goby指纹和Poc的提取方法 (已完结)
  - 题目：https://t.zsxq.com/eyfybqv
- 第二期：调用goby指纹的识别扫描 (已完结)
  - 题目：https://t.zsxq.com/0biSDRsQt
- 第三期：兼容社区PoC的通用验证工具 (已完结)
  - 题目: https://t.zsxq.com/UF2BMvJ
- 第四期：刷src的xss扫描器(已完结)
  - 题目: https://t.zsxq.com/rV3JqrB
- 第五期：web 动态爬虫（进行中）
  - 题目：https://t.zsxq.com/0b3U08Slv
- 第六期：训练自己的网络安全大模型
  - 题目：https://t.zsxq.com/18uy7yyYU

## 安全补全计划

### 恶意软件篇

1. 汇编与编译器
2. PE结构
3. ELF结构
   1. [ELFLoader](https://t.zsxq.com/057UF2nQf)

4. 进程
5. WoW64
6. shellcode
7. 注入技术
8. PE Loader
9. Hooking
10. 维权
11. UAC bypass
12. 横向移动
13. 对抗
    1. [一个免杀的框架，它的思想和工作流应该是武器化应有的样子](https://t.zsxq.com/ieamiYn)
    2. [对NTFS transactions的研究](https://t.zsxq.com/RNVbeim)

14. 混淆
15. Windows 内核模式下恶意软件
16. Linux rootKit
    1. [linux rootkit 入门](https://t.zsxq.com/NFeiM3N)

17. Golang与红队开发
    1. go-strip
       1. [go-strip v3.0源码](https://t.zsxq.com/05YVzFaiq)  
       2. [go-strip 更新啦 v2.0 成品+源码](https://t.zsxq.com/rzvRnEm)
       3. [go-strip 1.0的源码](https://t.zsxq.com/6IurbMR)

    2. [基于Golang的免杀总结](https://t.zsxq.com/057I2BY3F)
    3. [Golang红队开发指南](https://t.zsxq.com/05eamI2Zb)
    4. [garble原理研究](https://t.zsxq.com/05QzfyBmi)




### 自动化扫描篇

1. http(s) 请求
2. 指纹识别
   1. [Goby指纹的提取和YARA逆向](https://t.zsxq.com/q7E2Nfe)
   1. [Golang版的TideFinger](https://t.zsxq.com/05AEU7yB6)
   
3. 子域名与爆破
   1. [ksubdomain新版发布，github action 自动编译三平台](https://t.zsxq.com/uzjAQbu)

4. 端口扫描
    1. [像fofa一样解析RDP信息](https://t.zsxq.com/09nOE6IIC)
    2. [golang实现nmap os detection](https://t.zsxq.com/09qFwd3x6)
    
5. PoC验证与集成
   1. [w14scan 更新啦，开放源码！ 完成了第三期作业 《兼容xray和nuclei的poc验证工具》](https://t.zsxq.com/27UJm2v)
   1. [woodpecker](https://t.zsxq.com/05By33bae)
   
6. 扫描规则
   1. [域传送批量检测 Go源码](https://t.zsxq.com/022RV7e6U) 
   1. [log4j被动检测](https://t.zsxq.com/053ZnUJqv)
   
7. XSS扫描器
   - xscan扫描器，输入url自动化爬虫+XSS扫描，bugbounty挖洞神器
    - https://t.zsxq.com/0bcRm0Sp4 xscan v1.4 更新发布
    - https://t.zsxq.com/02au3FMFM xscan 更新 v1.2 
    - https://t.zsxq.com/02MBaAiqv xscan v0.8
    - https://t.zsxq.com/02uz7iuzr xscan v0.1 发布
   - dom-xss-scan 开源
    - https://t.zsxq.com/0dD7RF9YW
8. 爬虫
   1. crawlergo源码的学习
      - crawlergo源码的学习，以前就想写动态爬虫了，因为能原生干很多事情，现在终于可以试试了.准备写一份更新在知识星球 (又开一坑)
      - https://t.zsxq.com/JIYNNNR
      - https://t.zsxq.com/JYbuBEQ
      - https://t.zsxq.com/6MNfauz

9. bugbounty
    - [我自动化获得微软漏洞赏金的经历](https://t.zsxq.com/a6Aie2f)
    - [我的xss bugbounty自动化步骤](https://t.zsxq.com/05jIqrnEu)

10. 其他
    - [计算最短CIDR](https://t.zsxq.com/05au3bieQ) 
    - [随机化扫描算法Go实现](https://t.zsxq.com/09JHV6FTA)
    - [一个Go协程可取消的并发模型](https://t.zsxq.com/09YztbRVD)
    - [资产收集之spf记录](https://t.zsxq.com/09JC1feZW)
    - [退避重试算法](https://t.zsxq.com/0baRkmawG)
    - [web扫描中重定向问题](https://t.zsxq.com/0b1ewVIjN)

### 自动化脚本篇

- 模拟点击
- 颜色识别
- 图片识别
- 文字识别
- 验证识别
  - [通用验证码识别库源码，可以识别英数+汉字](https://t.zsxq.com/u7AyFe6)


### 漏洞与研究篇

1. CVE-2022-0847 Linux DirtyPipe 内核提权与docker逃逸 #go

   - https://t.zsxq.com/fE233RZ

   - https://t.zsxq.com/fE233RZ

   - https://t.zsxq.com/NJaAyVz

   - https://t.zsxq.com/NJaAyVz

2. [宝塔的研究](https://t.zsxq.com/BU72BEI)

3. [某C2鸡肋漏洞分析](https://t.zsxq.com/05miUnIai)

4. [复现Fastjson1.2.80漏洞](https://t.zsxq.com/05RFiIQbM)

### 武器化开发篇

- 微信聊天记录解密
  - [通用的内存微信获取个人信息方式](https://t.zsxq.com/QbIy7UZ)
    - 通过定位到微信内部的数据结构获取微信个人信息，不需要每个版本定位内存偏移

- 文件系统分析平台
  - [everything导出数据](https://t.zsxq.com/05ubIq3na)

- dll劫持 白加黑自动化改造
  - https://t.zsxq.com/ZRZRbUB
  - https://t.zsxq.com/Ju7aMzf
  - https://t.zsxq.com/EeiieY7
  - https://t.zsxq.com/Qv3BUny
  - https://t.zsxq.com/NfAaQje
  - https://t.zsxq.com/QZjY76Y
  - https://t.zsxq.com/v3RRrrz
  - https://t.zsxq.com/rNrBA6m
- dll自动化劫持
  - [100行代码实现通用劫持dll](https://t.zsxq.com/05ZrjEiEe)
  - [代理DLL自动生成，构建转发导出表(Go源码)](https://t.zsxq.com/05aYByVFy)

- 资产扫描管理系统
- RAT
  - [Go Rat + electron](https://t.zsxq.com/JE27iea)
  - [BIOPASS RAT 源码](https://t.zsxq.com/qR3nmuV)
  - [xss spoof欺骗模块](https://t.zsxq.com/jmUZVVb)
- 内存马
  - [内存马生成框架](https://t.zsxq.com/05nEqB6uv)


### 工具与原理篇

- [sliver c2相关的原理](https://t.zsxq.com/ny7IIUj)
- [Windows补丁对比工具是怎么做的？](https://t.zsxq.com/6yv7AEi)
- [ssrfmap 原理](https://t.zsxq.com/z7yFIIE)
- [dom-based-xss-finder 采用AST+js动态hook查找dom-xss的原理](https://t.zsxq.com/6YfEAeE)
  - dom-based-xss-finder 自动查找dom-xss的原理。dom-based-xss-finder是一个chrome插件，采用AST语法解析、js动态hook的方式来检测dom-xss，并会给出对应的调用堆栈。
- [XssSnpier原理](https://t.zsxq.com/2RbuZ7U)
  - XssSnpier，是来自3600kee的一个检测xss的chrome插件，看了一下它的大概原理，基于fuzz和基于监控error报错信息的半自动插件。
- [dalfox源码学习](https://t.zsxq.com/3rZbi2r)
  - 在信息流上看到有人star这个项目，dalfox是一个基于golang的xss扫描器，介绍说基于golang/DOM parser。
- CS上线器源码和相关原理
  - https://t.zsxq.com/uVnqjyb
  - https://t.zsxq.com/jyfAynI
- [对SigFlip(将数据隐写到已签名的PE文件上)的原理探究](https://t.zsxq.com/EIeqV7y)
- [读读fingerprintx，一个端口识别工具](https://t.zsxq.com/09a9GMJZg)
- [把玩donut](https://t.zsxq.com/09YN1UB3i)

### 其他想法

这个篇章记录那些不靠谱的奇思妙想

- [让小8机器人🤖当自己的todo list](https://t.zsxq.com/05mMZ3faa)
- [有一个想法，给所有安全类的电子书，pdf，一些演讲的ppt做全文索引，丰富hacking8的搜索功能](https://wx.zsxq.com/dweb2/index/tags/%E6%88%91%E6%9C%89%E4%B8%80%E4%B8%AA%E6%83%B3%E6%B3%95/28851452288141)
- [用golang实现桌面级全文索引](https://t.zsxq.com/09o8L21s0)
- [chatgpt与黑客知识库](https://t.zsxq.com/0bCU2vIuY)
