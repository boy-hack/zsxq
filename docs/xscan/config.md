# XSCAN 配置详解

## config.yaml 配置文件

高阶玩家可自行修改配置，达到最好的效果。以下是完整的配置文件说明：

## 基础配置

### 调试与代理设置

```yaml
debug: True # 调试模式
proxy: ""   # 代理配置
```

#### 配置说明

- **debug**: 启用调试模式，会输出详细的调试信息，便于排查问题和了解扫描过程
- **proxy**: HTTP代理配置，格式为 `http://proxy_host:port` 或 `socks5://proxy_host:port`，留空则不使用代理

#### 使用场景

- **调试模式**: 首次使用或遇到问题时建议开启，正式使用时可关闭以减少日志输出
- **代理配置**: 在需要通过代理访问目标、隐藏真实IP或绕过网络限制时使用

### Headers 配置

```yaml
headers: # 网页header
  User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 11_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.88 Safari/537.36
```

#### 配置说明

- **User-Agent**: 自定义浏览器标识，模拟真实浏览器行为
- 可添加其他HTTP头：如 `Referer`、`Accept-Language`、`Authorization` 等

#### 最佳实践

```yaml
headers:
  User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36
  Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
  Accept-Language: zh-CN,zh;q=0.9,en;q=0.8
  Accept-Encoding: gzip, deflate
  Connection: keep-alive
```

## GAU 配置

```yaml
gau:
  enable: False # 启用gau
  include_sub: True # 是否包含子域名
  with_spider: True # 是否再爬虫获取更多url
```

### GAU (GetAllUrls) 说明

GAU是一个被动URL收集工具，可以从多个数据源收集历史URL：

#### 配置详解

- **enable**: 是否启用GAU功能，开启后会从第三方数据源收集URL
- **include_sub**: 是否包含子域名的URL，建议开启以获得更全面的URL覆盖
- **with_spider**: GAU收集到URL后是否再次进行爬虫，建议开启以发现更多链接

#### 数据源

GAU会从以下数据源收集URL：
- **Wayback Machine**: 互联网档案馆的历史页面
- **Common Crawl**: 开源网页爬虫数据
- **Virus Total**: 安全厂商的URL情报
- **URLScan**: 网页扫描服务的数据

## 爬虫配置

```yaml
spider: # 爬虫设置
  concurrency: 500 # 爬虫并发数量
  limit: 30 # 每秒限制并发数量
  timeout: 20
  max_depth: 12                     # 最大页面深度限制
  max_page_visit_per_site: 5000     # 每个站点最多访问的页面数量
  crawler_priority: depth-first # 爬虫优先级算法 depth-first 深度优先 breadth-first 广度优先
  no_scope: False # 指定此参数，爬虫将不受范围限制，但是受最大深度限制
  only_root_scope: False  # 只限制根域名范围，如www.baidu.com，将限制爬虫范围为 *.baidu.com
```

### 性能控制参数

#### 并发与限速

- **concurrency: 500**: 爬虫并发数量，建议根据目标网站承受能力调整
  - 小型网站: 50-100
  - 中型网站: 200-300  
  - 大型网站: 500-1000
- **limit: 30**: 每秒请求限制，避免对目标造成过大压力
- **timeout: 20**: 单个请求超时时间（秒），网络较慢时可适当增加

#### 深度与范围控制

- **max_depth: 12**: 最大爬虫深度，从起始URL开始的最大跳转层数
- **max_page_visit_per_site: 5000**: 每个站点最多访问页面数，防止爬虫陷入无限循环
- **crawler_priority**: 爬虫优先级算法
  - `depth-first`: 深度优先，优先爬取更深层的页面
  - `breadth-first`: 广度优先，优先爬取同层级的页面

#### 范围限制

- **no_scope: False**: 是否受范围限制
  - `True`: 不受域名范围限制，但受深度限制
  - `False`: 严格按照域名范围爬取
- **only_root_scope: False**: 是否只限制根域名
  - `True`: 如输入`www.example.com`，爬取范围为`*.example.com`
  - `False`: 严格按照输入的域名爬取

### 相似度过滤配置

#### URL泛化过滤

```yaml
  similarity_url: # 启用Url泛化过滤相同网站
    use: False  # 是否启用
    threshold: 10 #url泛化阈值
```

**功能说明**: 通过URL模式识别过滤相似的URL结构

**使用场景**: 
- 电商网站的商品页面：`/product/{id}`
- 用户资料页面：`/user/{uid}`
- 文章详情页面：`/article/{aid}`

**配置建议**:
- 内容管理系统: `threshold: 5-10`
- 电商平台: `threshold: 20-50`
- 社交网站: `threshold: 10-30`

#### DOM相似度过滤

```yaml
  similarity_page_dom: # 启用DOM相似度算法过滤相同网站
    use: True # 是否启用
    threshold: 5 # 网站阈值，同个domain相似度大于这个数开启过滤
    similarity: 0.95 # 相似度阈值，大于这个数判定相似
    vector_dim: 5000 # 向量维度
```

**技术原理**: 
- 将页面DOM结构转换为向量
- 计算向量间的余弦相似度
- 过滤相似度超过阈值的页面

**参数调优**:
- **threshold: 5**: 同域名下发现5个以上相似页面时开启过滤
- **similarity: 0.95**: 相似度阈值，越高过滤越严格
  - 模板网站: 0.98-0.99 (页面结构高度相似)
  - 动态网站: 0.90-0.95 (页面内容变化较大)
  - 个人博客: 0.85-0.90 (页面布局相对简单)
- **vector_dim: 5000**: 向量维度，影响计算精度和性能

#### 简单Hash去重

```yaml
  simile_hash: # 简单hash算法去重
    use: False
```

**功能说明**: 基于页面内容的简单哈希去重，速度快但精度较低

**使用建议**: DOM相似度过滤已经足够精确，通常不需要开启

### 数据源与字典配置

```yaml
  sources: # 使用哪些源获得更多url
    - robotstxt
    - sitemapxml
  spider_rule_dir: ./spider_rules # 规则文件目录
  directory_dict: ./dict # 目录字典，会扫描相关目录
```

#### URL数据源

- **robotstxt**: 从`robots.txt`文件中提取URL和路径信息
- **sitemapxml**: 从`sitemap.xml`文件中获取站点地图URL


#### 目录字典

- **directory_dict**: 常见目录和文件的字典路径
- 内置常见目录: `admin/`, `backup/`, `test/`, `api/` 等

### 访问控制配置

```yaml
  black_list: # 黑名单
    - ".google.com"
    - ".facebook.com"
  cookies:
    "*.example.com": "cookie1=1;cookie2=2"
    "a.example2.com": "cookie3=3;cookie4=4"
```

#### 黑名单配置

**功能说明**: 防止爬虫访问第三方域名或无关网站

**配置示例**:
```yaml
black_list:
  - ".google.com"
  - ".facebook.com"
  - ".twitter.com"
  - ".linkedin.com"
```

#### Cookie配置（新增功能）

**功能说明**: 为不同域名配置不同的Cookie，支持通配符匹配

**使用场景**:
- **登录状态**: 配置登录后的Session Cookie
- **多子域**: 为不同子域名配置专用Cookie
- **A/B测试**: 配置特定的测试Cookie

**配置示例**:
```yaml
cookies:
  "*.example.com": "sessionid=abc123;csrftoken=def456"
  "admin.example.com": "admin_token=xyz789;role=admin"
  "api.example.com": "api_key=key123;version=v2"
```

## 扫描器配置

```yaml
scan: # 扫描器配置
  concurrency: 300 # 扫描器并发数量
  limit: 30 # 每秒限制并发数量
  filter_threshold: 30 # 防止重复的xss报告，每个域名xss最多报告的阈值
  found_hidden_parameter: True # 从页面中发现隐藏参数
  found_hidden_parameter_from_js: False
  parameter_group_size: 40
  timeout: 30 # 超时时间 单位(秒)
```

### 性能参数

- **concurrency: 300**: 扫描器并发数量，影响扫描速度
- **limit: 30**: 每秒扫描请求限制，避免触发WAF
- **timeout: 30**: 扫描请求超时时间

### 参数发现配置

#### 隐藏参数发现

- **found_hidden_parameter: True**: 从HTML页面中发现隐藏的input参数
- **found_hidden_parameter_from_js: False**: 从JavaScript代码中发现参数（新增功能）

**JavaScript参数发现**:
- 分析JS中的AJAX请求
- 提取API接口参数
- 识别动态生成的参数

#### 参数处理优化

- **parameter_group_size: 40**: 参数分组大小，影响扫描效率
- **filter_threshold: 30**: 每个域名最多报告的XSS漏洞数量，防止重复报告

### 扫描位置配置

```yaml
  position: # 扫描参数位置，可选 get,post,uri,header,cookie
    - get
    - post
    - uri
```

#### 支持的注入位置

- **get**: URL查询参数
- **post**: POST请求体参数
- **uri**: URL路径参数
- **header**: HTTP请求头（可选）
- **cookie**: Cookie参数（可选）

### 输出配置

```yaml
  output: # 支持生成json和markdown格式，为空则不生成
    response: False # 保存返回包
    response_header: True # 保存返回header
```

#### 输出选项

- **response: False**: 是否保存完整的HTTP响应内容
  - 开启后会增加存储空间占用
  - 便于漏洞验证和分析
- **response_header: True**: 是否保存HTTP响应头
  - 用于分析服务器信息
  - 检测安全头配置

### 隐藏参数字典

```yaml
  hidden_parameters: # 内置用于GET探测的隐藏参数
    - key
    - redirect
    - region
    - action
    - l
```

#### 内置参数说明

这些是从实战经验中总结的常见隐藏参数：

- **key**: 密钥参数，常用于加密和验证
- **redirect**: 重定向参数，容易出现开放重定向漏洞
- **region**: 地区参数，可能影响页面内容
- **action**: 操作参数，指定要执行的动作
- **l**: 语言参数，影响页面显示语言

## 通知配置

```yaml
report: # 结果推送,填写对应参数则使用，为空则不使用
  finish_notify: True # 扫描完毕通知
  node_name: 节点001 # 节点的名称，通知的时候会带上
  bark:
    server:
    token:
  dingding:
    token:
    secret:
  feishu:
    token:
    secret:
```

### 通知基础配置

- **finish_notify: True**: 扫描完成后是否发送通知
- **node_name**: 节点名称，多节点部署时用于区分

### 支持的通知方式

#### Bark通知（iOS推送）

```yaml
bark:
  server: https://api.day.app/your_device_key/
  token: your_bark_token
```

#### 钉钉机器人

```yaml
dingding:
  token: your_dingtalk_webhook_token
  secret: your_dingtalk_secret_key
```

#### 飞书机器人

```yaml
feishu:
  token: your_feishu_webhook_token
  secret: your_feishu_secret_key
```

## 配置优化建议

### 性能调优

#### 高性能配置（适用于大型目标）

```yaml
spider:
  concurrency: 1000
  limit: 50
  max_page_visit_per_site: 10000
  similarity_page_dom:
    similarity: 0.98
scan:
  concurrency: 500
  parameter_group_size: 60
  filter_threshold: 50
```

#### 精确扫描配置（适用于小型目标）

```yaml
spider:
  concurrency: 100
  limit: 10
  max_depth: 20
  similarity_page_dom:
    similarity: 0.90
scan:
  concurrency: 50
  found_hidden_parameter_from_js: True
  parameter_group_size: 20
```

### 隐蔽性配置

```yaml
spider:
  concurrency: 50
  limit: 5
  timeout: 60
headers:
  User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36
  Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
  Accept-Language: en-US,en;q=0.5
  Connection: keep-alive
  Upgrade-Insecure-Requests: 1
```

### 特定场景配置

#### SPA单页应用

```yaml
spider:
  spider_with_rule: True
  found_hidden_parameter_from_js: True
  max_depth: 8
  similarity_page_dom:
    similarity: 0.85
```

#### 大型电商网站

```yaml
spider:
  similarity_url:
    use: True
    threshold: 50
  max_page_visit_per_site: 20000
scan:
  filter_threshold: 100
```

#### 企业内网测试

```yaml
spider:
  concurrency: 200
  limit: 20
  only_root_scope: False
  no_scope: False
scan:
  found_hidden_parameter_from_js: True
  output:
    response: True
    response_header: True
``` 