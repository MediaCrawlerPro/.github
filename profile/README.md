## MediaCrawler Pro版本诞生的背景
[MediaCrawler](https://github.com/NanmiCoder/MediaCrawler)这个项目开源至今获得了大量的关注，同时也暴露出来了一系列问题，比如：
- 能否支持多账号？
- 能否在linux部署？
- 能否去掉playwright的依赖？
- 有没有更简单的部署方法？
- 有没有针对新手上门槛更低的方法？
- 能不能提供可视化的界面操作？
- 能不能提供API的版本？

诸如上面的此类问题，想要在原有项目上去动刀，无疑是增加了复杂度，可能导致后续的维护更加困难。
出于可持续维护、简便易用、部署简单等目的，对MediaCrawler进行彻底重构。

## 项目介绍
### [MediaCrawler](https://github.com/NanmiCoder/MediaCrawler)的Pro版本python实现
**小红书爬虫**，**抖音爬虫**， **快手爬虫**， **B站爬虫**， **微博爬虫**，**百度贴吧**...。

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
| 微博   | ✅     | ✅        | ✅    | ❌       | ✅         |
| 百度贴吧 | ✅     | ✅        | ✅    | ❌       | ✅         |
| 抖音   | ❌     | ❌        | ❌    | ❌       | ❌         |
| 快手   | ❌     | ❌        | ❌    | ❌       | ❌         |
| B 站  | ❌     | ❌        | ❌    | ❌       | ❌         |


## 待办事项
- [x] 账号池管理与IP代理池逻辑彻底重构 
- [X] 账号支持excel和mysql两种管理方式
- [x] 小红书爬虫重构
- [x] 微博爬虫重构
- [x] 百度贴吧爬虫重构
- [ ] B站爬虫重构
- [ ] 抖音爬虫重构
- [ ] 快手爬虫重构
- [ ] 封装成API版本
- [ ] 提供可视化界面
- [ ] 提供Golang语言版本

## 学习和获取Pro版本的访问权限
> MediaCrawler开源超过一年了，相信该仓库帮过不少朋友低门槛的学习和了解爬虫。维护真的耗费了大量精力和人力<br>
> 所以Pro版本不会开源，可以订阅Pro版本让我更加有动力去更新。<br>
> 从MediaCrawler到Pro版本发生了一些底层逻辑转变，可以从中学习代码的一些设计思路，帮助你更好的理解代码的设计和实现。
<div>
    <img src="../img.png" alt="" height="300px">
</div> 

备注：扫码支付之后（备注你的github用户名，我会尽快开通仓库访问权限）。若需详细了解Pro版本可以加我微信：`yzglan`，备注：pro版本


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
> 虽然我们提供了IP代理池的支持，但是还是得跟大家再次强调下，不要对一些自媒体平台进行大规模爬虫或其他非法行为，要踩缝纫机的哦🤣<br>
> 虽然都是公开数据，但是在国内的法律环境下，还是要注意一些规则的。切勿用于非法用途。切勿用于商业用途。

本仓库的所有内容仅供学习使用，禁止用于商业用途。任何人或组织不得将本仓库的内容用于非法用途或侵犯他人合法权益。

我们提供的爬虫仅能获取抖音、快手、哔哩哔哩、小红书、百度贴吧、微博平台上**公开的信息**，

我们强烈反对任何形式的隐私侵犯行为。如果你使用本项目进行了侵犯他人隐私的行为，我们将与你保持距离，并支持受害者通过法律手段维护自己的权益。<br>

对于因使用本仓库内容而引起的任何法律责任，本仓库不承担任何责任。使用本仓库的内容即表示您同意本免责声明的所有条款和条件<br>

