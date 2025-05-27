<!--
 * @Author: wzdnzd
 * @Date: 2022-03-06 14:51:29
 * @Description: 
 * Copyright (c) 2022 by wzdnzd, All Rights Reserved.
-->

## 功能
打造免费代理池，爬一切可爬节点
> 拥有灵活的插件系统，如果目标网站特殊，现有功能未能覆盖，可针对性地通过插件实现

> 欢迎 Star 及 PR。对于质量较高且普适的爬取目标，亦可在 Issues 中列出，将在评估后选择性添加

## 使用方法
> 可前往 [Issue #91](https://github.com/wzdnzd/aggregator/issues/91) 食用**共享订阅**，量大质优。**请勿浪费**
 
略，自行探索。我才不会告诉你入口是 `collect.py` 和 `process.py`。**强烈建议使用后者，前者只是个小玩具**，配置参考 `subscribe/config/config.default.json`，详细文档见 [DeepWiki](https://deepwiki.com/wzdnzd/aggregator)



在`wzdnzd/aggregator`这个项目中，`collect.py`和`process.py`是两个核心的 Python 脚本文件，分别承担**数据采集** 和**数据处理** 的不同职责。它们是整个代理节点聚合流程的关键组成部分。





### 1.节点采集器（订阅收集）

#### 功能简介：

`collect.py`是负责**从远程订阅链接获取代理配置信息** 的脚本。它会抓取用户提供的订阅地址中的节点数据，并将这些原始数据保存下来，供后续处理使用。

#### 主要作用：

*   **下载订阅链接内容** （如 Clash 或 V2Ray 的订阅 URL）
*   **提取节点信息** （IP、端口、加密方式、密码等）
*   **保存原始节点数据** 到本地（通常是 JSON 文件或临时缓存）

#### 使用方式示例：

    !python -u subscribe/collect.py -s

*   `-s`参数通常表示“silent mode”或“start”，即静默启动或立即开始采集任务。

#### 输出结果：

*   采集完成后，节点数据会被保存在项目目录下，`/content/aggregator/data/clash.yaml`或直接生成`clash.yaml`配置文件。


### 2.节点处理器

#### 功能简介：

`process.py`是更高级的脚本，用于对`collect.py`收集来的原始节点数据进行**清洗、去重、过滤、测速、排序等处理操作** ，最终输出一个优化后的代理节点配置文件（如`clash.yaml`）。

#### 主要作用：

*   **去重** ：去除重复的节点。
*   **过滤** ：根据规则（如国家、延迟、协议支持）筛选有效节点。
*   **测速** ：通过 ping、HTTP 请求等方式测试节点速度。
*   **排序** ：按延迟、稳定性等指标排序。
*   **格式转换** ：将节点数据转换为 Clash、Surge 等客户端支持的格式。

## 免责申明
+ 本项目仅用作学习爬虫技术，请勿滥用，不要通过此工具做任何违法乱纪或有损国家利益之事
+ 禁止使用该项目进行任何盈利活动，对一切非法使用所产生的后果，本人概不负责

## 致谢
1. <u>[Subconverter](https://github.com/asdlokj1qpi233/subconverter)</u>、<u>[Mihomo](https://github.com/MetaCubeX/mihomo)</u>

2. 感谢 [![YXVM](https://support.nodeget.com/page/promotion?id=250)](https://yxvm.com)
[NodeSupport](https://github.com/NodeSeekDev/NodeSupport) 赞助了本项目
