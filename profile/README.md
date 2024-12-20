## 免责声明
> 本项目的所有内容仅供学习和参考之用，禁止用于商业用途。任何人或组织不得将本仓库的内容用于非法用途或侵犯他人合法权益。
> 
> 点击查看更为详细的免责声明。[点击跳转](#disclaimer)

## MediaCrawler Pro版本诞生的背景
[MediaCrawler](https://github.com/NanmiCoder/MediaCrawler)这个项目开源至今获得了大量的关注，同时也暴露出来了一系列问题，比如：
- 能否支持多账号？
- 能否在linux部署？
- 能否去掉playwright的依赖？
- 有没有更简单的部署方法？
- 有没有针对新手上门槛更低的方法？

诸如上面的此类问题，想要在原有项目上去动刀，无疑是增加了复杂度，可能导致后续的维护更加困难。
出于可持续维护、简便易用、部署简单等目的，对MediaCrawler进行彻底重构。

## 项目介绍
### [MediaCrawler](https://github.com/NanmiCoder/MediaCrawler)的Pro版本python实现
**小红书爬虫**，**抖音爬虫**， **快手爬虫**， **B站爬虫**， **微博爬虫**，**百度贴吧**，**知乎爬虫**...。

支持多种平台的爬虫，支持多种数据的爬取，支持多种数据的存储，最重要的**完美支持多账号+IP代理池，让你的爬虫更加稳定**。
相较于MediaCrawler，Pro版本最大的变化：
- 去掉了playwright的依赖，不再将Playwright集成到爬虫主干中，依赖过重。
- 增加了Docker，Docker-compose的方式部署，让部署更加简单。
- 多账号+IP代理池的支持，让爬虫更加稳定。
- 新增签名服务，解耦签名逻辑，让爬虫更加灵活。

## 功能列表
| 平台   | 关键词搜索 | 指定帖子ID爬取 | 二级评论 | 指定创作者主页 | 账号池+IP代理池 | 
|------|-------|----------|------|---------|-----------|
| 小红书  | ✅     | ✅        | ✅    | ✅       | ✅         |
| 微博   | ✅     | ✅        | ✅    | ✅       | ✅         |
| 百度贴吧 | ✅     | ✅        | ✅    | ✅       | ✅         |
| B 站  | ✅     | ✅        | ✅    | ✅       | ✅         |
| 抖音   | ✅     | ✅        | ✅    | ✅      | ✅         |
| 快手   | ✅     | ✅        | ✅    | ✅       | ✅         |
| 知乎   | ✅     | ✅        | ✅    | ✅       | ✅         |

## 获取Pro版本的访问权限
> 如果感兴趣可以加我微信，订阅Pro版本访问权限哦，有门槛💰。<br>
> 
> ⚠️⚠️仅针对想学习Pro版本源码实现的用户，如果是公司或者商业化盈利性质的就不要加我了，谢谢🙏 
> 
> 代码设计拓展性强，可以自己扩展更多的爬虫平台，更多的数据存储方式，相信对你架构这种爬虫代码有所帮助。

扫描下方我的个人微信，备注：pro版本（如果图片展示不出来，可以直接添加我的微信号：yzglan）

<div style="max-width: 200px">  
<p><img alt="relakkes_wechat" src="../relakkes_weichat.JPG" style="width: 200px;height: 100%" ></p>
</div>



## 待办事项
- [x] 账号池管理 & 支持excel和mysql两种方式
- [x] 小红书爬虫重构
- [x] 微博爬虫重构
- [x] 百度贴吧爬虫重构
- [x] B站爬虫重构
- [x] 抖音爬虫重构
- [x] 快手爬虫重构
- [x] Pro版本使用教程视频录制
- [x] 知乎关键词爬虫支持
- [x] 知乎创作者主页爬虫支持
- [x] 知乎指定帖子支持
- [ ] MediaCrawlerPro-Golang版本开发
- [ ] AI分析总结


## 源代码仓库列表：
`MediaCrawlerPro-Python`和`MediaCrawlerPro-SignSrv`

### MediaCrawlerPro-Python
> 该项目是MediaCrawler的Pro版本的python实现，主要是对MediaCrawler进行了重构，去掉了playwright的依赖，增加了多账号+IP代理池的支持等等。

#### 目录结构
```
MediaCrawlerPro-Python目录结构如下所示：
.  
├── base                                # 基础类目录  
│   └── base_crawler.py                 # 抽象类定义  
├── cmd_arg                             # 命令行参数目录
│   └── arg.py                          # 命令行参数解析  
├── config                              # 配置文件目录  
│   ├── README.md                       # 配置文件说明  
│   ├── accounts_cookies.xlsx           # excel账号池模板  
│   ├── base_config.py                  # 基础配置  
│   ├── db_config.py                    # 数据库配置  
│   ├── proxy_config.py                 # 代理配置  
│   └── sign_srv_config.py              # 签名服务配置  
├── constant                            # 常量目录  
│   ├── baidu_tieba.py                  # 百度贴吧常量  
│   ├── base_constant.py                # 基础常量  
│   ├── weibo.py                        # 微博常量  
│   └── xiaohongshu.py                  # 小红书常量  
├── media_platform                      # 平台爬虫实现目录  
│   ├── tieba                           # 百度贴吧爬虫实现  
│   │   ├── client.py                   # 贴吧客户端API  
│   │   ├── core.py                     # 主流程逻辑  
│   │   ├── field.py                    # 字段定义  
│   │   └── help.py                     # 辅助函数  
│   ├── weibo                           # 微博爬虫实现  
│   │   ├── client.py                   # 微博客户端API   
│   │   ├── core.py                     # 主流程逻辑  
│   │   ├── exception.py                # 异常定义处理  
│   │   ├── field.py                    # 字段定义  
│   │   └── help.py                     # 辅助函数  
│   └── xhs                             # 小红书爬虫实现  
│       ├── client.py                   # 小红书客户端API  
│       ├── core.py                     # 主流程逻辑  
│       ├── exception.py                # 异常定义处理    
│       ├── field.py                    # 字段定义  
│       └── help.py                     # 辅助函数  
├── model                               # 数据模型目录  
│   ├── m_baidu_tieba.py                # 百度贴吧数据模型  
│   ├── m_weibo.py                      # 微博数据模型  
│   └── m_xiaohongshu.py                # 小红书数据模型  
├── pkg                                 # 项目包目录  
│   ├── account_pool                    # 账号池目录  
│   │   ├── field.py                    # 字段定义  
│   │   └── pool.py                     # 账号池实现  
│   ├── cache                           # 缓存目录  
│   │   ├── abs_cache.py                # 缓存抽象类  
│   │   ├── cache_factory.py            # 缓存工厂  
│   │   ├── local_cache.py              # 本地缓存  
│   │   └── redis_cache.py              # redis缓存  
│   ├── proxy                           # IP代理目录  
│   │   ├── providers                   # IP代理提供商目录   
│   │   ├── base_proxy.py               # IP代理抽象类  
│   │   ├── proxy_ip_pool.py            # IP代理池实现  
│   │   └── types.py                    # IP代理类型定义  
│   ├── rpc                             # RPC目录  
│   │   └── sign_srv_client             # 签名服务客户端  
│   └── tools                           # 工具目录  
│       ├── crawler_util.py             # 爬虫工具函数  
│       ├── time_util.py                # 时间工具函数  
│       └── utils.py                    # 通用工具函数  
├── repo                                # 数据存储目录  
│   ├── accounts_cookies                # 账号池相关的存储  
│   │   └── cookies_manage_sql.py       # mysql账号池管理
│   └── platform_save_data              # 平台数据存储  
│       ├── tieba                       # 百度贴吧数据存储  
│       ├── weibo                       # 微博数据存储  
│       └── xhs                         # 小红书数据存储  
├── schema                              # 数据库表结构目录  
│   └── tables.sql                      # 数据库表结构  
├── static                              # 静态文件目录  
│   ├── img.png  
│   ├── img3.png  
│   ├── img4.png  
│   ├── img_1.png  
│   └── img_2.png  
├── test                                # 单元测试目录  
│   ├── test_expiring_local_cache.py    # 本地缓存测试  
│   ├── test_proxy_ip_pool.py           # IP代理池测试  
│   ├── test_redis_cache.py             # redis缓存测试  
│   └── test_utils.py                   # 工具函数测试  
├── Dockerfile                          # Dockerfile  
├── LICENSE                             # 开源协议  
├── README.md                           # 项目说明  
├── async_db.py                         # 异步数据库  
├── db.py                               # 数据库初始化  
├── docker-compose.yaml                 # docker-compose文件  
├── main.py                             # 程序入口  
├── mypy.ini                            # mypy配置  
├── requirements.txt                    # 依赖  
└── var.py                              # 上下文变量定义
```
#### 安装文档
[MediaCrawlerPro-Python](https://github.com/MediaCrawlerPro/MediaCrawlerPro-Python)

### MediaCrawlerPro-SignSrv 平台请求签名服务
> 将请求签名的功能从MediaCrawler中独立出来，作为一个独立的服务，方便调用。

#### 目录结构
```
MediaCrawlerPro-SignSrv 目录结构说明
├── apis                          # API接口目录  
│   ├── base_handler.py           # Tornado Handler的基础类  
│   ├── douyin.py                 # 抖音签名API接口  
│   └── xiaohongshu.py            # 小红书签名API接口  
├── constant                      # 常量定义目录  
│   ├── base_constant.py          # 基础常量  
│   └── error_code.py             # 错误代码定义  
├── logic                         # 业务签名逻辑目录  
│   ├── douyin                    # 抖音签名业务逻辑  
│   │   └── douyin_logic.py       # 抖音签名业务逻辑实现  
│   └── xhs                       # 小红书签名业务逻辑  
│       ├── help.py               # 小红书辅助函数  
│       └── xhs_logic.py          # 小红书签名业务逻辑实现  
├── params                        # 参数定义目录  
│   ├── base_model.py             # 基础参数模型  
│   ├── douyin_sign.py            # 抖音签名相关参数  
│   └── xiaohongshu_sign.py       # 小红书签名相关参数  
├── pkg                           # 项目包目录  
│   ├── custom_exceptions         # 自定义异常目录  
│   │   └── base_exceptions.py    # 基础异常类  
│   ├── js                        # JavaScript目录  
│   │   ├── douyin.js             # 抖音相关JS文件  
│   │   ├── stealth.min.js        # 去除浏览器自动化特征的JS  
│   │   └── xhs.js                # 小红书相关JS文件  
│   ├── playwright                # Playwright目录  
│   │   ├── douyin_manager.py     # 抖音Playwright管理器  
│   │   ├── manager.py            # 通用Playwright管理器  
│   │   └── xhs_manager.py        # 小红书Playwright管理器  
│   └── utils                     # 工具函数目录  
│       ├── base_utils.py         # 基础工具函数  
│       └── crawler_util.py       # 爬虫工具函数  
├── Dockerfile                    # Docker配置文件  
├── LICENSE                       # 开源协议  
├── README.md                     # 项目说明文档  
├── app.py                        # 应用程序入口  
├── config.py                     # 配置文件  
├── context_vars.py               # 上下文变量定义    
├── requirements.txt              # 依赖项说明文件  
└── urls.py                       # URL路由配置
```
#### 安装文档
[MediaCrawlerPro-SignSrv](https://github.com/MediaCrawlerPro/MediaCrawlerPro-SignSrv)

## 免责声明
<div id="disclaimer"> 

### 1. 项目目的与性质
本项目（以下简称“本项目”）是作为一个技术研究与学习工具而创建的，旨在探索和学习网络数据采集技术。本项目专注于自媒体平台的数据爬取技术研究，旨在提供给学习者和研究者作为技术交流之用。

### 2. 法律合规性声明
本项目开发者（以下简称“开发者”）郑重提醒用户在下载、安装和使用本项目时，严格遵守中华人民共和国相关法律法规，包括但不限于《中华人民共和国网络安全法》、《中华人民共和国反间谍法》等所有适用的国家法律和政策。用户应自行承担一切因使用本项目而可能引起的法律责任。

### 3. 使用目的限制
本项目严禁用于任何非法目的或非学习、非研究的商业行为。本项目不得用于任何形式的非法侵入他人计算机系统，不得用于任何侵犯他人知识产权或其他合法权益的行为。用户应保证其使用本项目的目的纯属个人学习和技术研究，不得用于任何形式的非法活动。

### 4. 免责声明
开发者已尽最大努力确保本项目的正当性及安全性，但不对用户使用本项目可能引起的任何形式的直接或间接损失承担责任。包括但不限于由于使用本项目而导致的任何数据丢失、设备损坏、法律诉讼等。

### 5. 知识产权声明
本项目的知识产权归开发者所有。本项目受到著作权法和国际著作权条约以及其他知识产权法律和条约的保护。用户在遵守本声明及相关法律法规的前提下，可以下载和使用本项目。

### 6. 最终解释权
关于本项目的最终解释权归开发者所有。开发者保留随时更改或更新本免责声明的权利，恕不另行通知。
</div>

