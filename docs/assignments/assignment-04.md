# 第四期：刷src的xss扫描器

## 🎯 作业目标

- 从零开始，利用动态爬虫技术和浏览器引擎，构建一款能够自动化发现 XSS 漏洞的扫描器。

## 📖 作业背景

XSS (跨站脚本) 是 Web 漏洞中常见且危害较大的一种。自动化的 XSS 扫描器是 Bug Bounty 猎人和 SRC 刷分手的必备利器。传统的扫描器在处理由 JavaScript 动态渲染的现代 Web 应用时常常力不从心。

本期作业将挑战使用更先进的技术，构建一款效果更好、能够应对复杂前端应用的 XSS 扫描器。

## 📝 作业要求

1.  **集成动态爬虫**：
    -   选择并集成一款动态爬虫，如 `crawlergo`。
    -   编写代码调用爬虫，对目标 URL 进行爬取，获取尽可能多的请求（URL、表单等）。

2.  **参数分析与 Fuzz**：
    -   对爬虫收集到的请求进行分析，识别出所有可控的参数（URL query, body, header, cookie等）。
    -   对识别出的参数，使用精心设计的 XSS Payload 进行替换和Fuzz。

3.  **漏洞检测引擎**：
    -   **核心要求**：利用浏览器引擎（如 `Chrome DevTools Protocol`）来渲染带有 Payload 的页面。
    -   通过监听浏览器的事件（如 `alert`, `confirm`, `prompt`）或检查 DOM 结构的变化，来判断 XSS Payload 是否被成功执行。
    -   这种基于真实浏览器环境的检测方式，可以有效地发现 DOM-based XSS，并大大降低误报率。

4.  **结果输出**：
    -   当检测到 XSS 漏洞时，输出漏洞 URL 和有效的 Payload。
    -   （选做）提供漏洞的上下文信息，如触发点在 DOM 中的位置。

5.  **成果展示**：
    -   提供你的 XSS 扫描器源代码。
    -   使用你的工具，在一个已知的 XSS 测试网站（如 `testphp.vulnweb.com`）上发现漏洞。

## 💡 核心思路与提示

-   **Chrome DevTools Protocol (CDP)**：是实现本作业的关键。你可以使用 `pyppeteer` (Python), `puppeteer` (Node.js) 或 `chromedp` (Go) 等库来控制浏览器。
-   **Payload 设计**：Payload 不仅仅是 `<script>alert(1)</script>`。设计一些能够触发 DOM 事件、闭合标签的 Payload 会更有效果。
-   **去重**：在扫描过程中，可能会发现大量由同一个漏洞点触发的 XSS。需要设计去重逻辑，将它们归并为同一个漏洞。

## 🔗 参考链接

-   **题目链接**: [https://t.zsxq.com/rV3JqrB](https://t.zsxq.com/rV3JqrB)
-   **相关项目**: 星球专属工具 **XScan** 就是该作业的终极形态,xscan第一版本已在星球开源。

---

> 这是星球含金量最高的作业之一，完成它，你将对 XSS 漏洞和现代 Web 应用的扫描技术有全新的认识。 