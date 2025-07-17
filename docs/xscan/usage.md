# XSCAN 使用指南

## 基础使用

### 配置文件

xscan将很多扫描参数抽离了出来，做成了配置文件。默认使用 `config.yaml` 配置文件，一般默认配置即可正常使用。

### 命令行帮助

大部分功能也可从命令行使用，如果配置文件和命令行指令相冲突，命令行指令优先级最高。

```bash
xscan --help
```

输出信息：
```
XSSCAN by w8ay. version:v3.6.3


NAME:
   XSSCAN - xss scanner

USAGE:
   XSSCAN [global options] command [command options]

VERSION:
   v3.6.3

COMMANDS:
   spider   爬虫+xss
   proxy    被动代理+xss
   agent    xscan作为扫描端，在线接收任务
   help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --config value      配置文件路径，默认为config.yaml (default: "config.yaml")
   --output-dir value  输出文件路径,默认为当前路径
   --help, -h          show help
   --version, -v       print the version
```



## Spider 模式（爬虫扫描）

一般使用这个模式，输入url就可以进行扫描了。漏洞默认以markdown和json格式输出。

### 单URL扫描

```bash
xscan spider -url xxx.com
```

### 从文件读取URL扫描

```bash
xscan spider -file urls.txt
```

### 查看Spider模式帮助

```bash
xscan spider -h
```

## Proxy 模式（被动代理）

### 生成证书

```bash
./xscan proxy --generate-ca
```

证书会生成到 `certs` 文件夹，需要信任 `cacert.pem` 证书。

### 启动被动代理

```bash
./xscan proxy
```

**默认代理地址**：`127.0.0.1:8080`

### 查看Proxy模式帮助

```bash
xscan proxy -h
```

## 配置选项

### 全局选项

- `--config value` : 配置文件路径，默认为config.yaml
- `--output-dir value` : 输出文件路径，默认为当前路径
- `--help, -h` : 显示帮助信息
- `--version, -v` : 显示版本信息

## 使用说明

1. **Spider模式**：主动爬虫扫描模式，输入目标URL后自动爬取并进行XSS测试
2. **Proxy模式**：被动代理扫描模式，类似于xray的工作方式，通过代理流量进行XSS检测
3. **无害检测**：所有XSS payload均为无害payload，不会对目标网站造成影响
