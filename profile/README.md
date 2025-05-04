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
- 多账号+IP代理池的支持，让爬虫更加稳定。
- 新增签名服务，解耦签名逻辑，让爬虫更加灵活。
- 新增自媒体平台视频下载器桌面端UI下载项目（适合全栈项目学习）。
- 支持多个平台的首页信息流推荐（HomeFeed）

## 功能列表
| 平台 | 关键词搜索 | 指定帖子ID爬取 | 二级评论 | 创作者主页 | 首页推荐信息流 |账号池+IP代理池 | 
|----|-------|----------|------|-------|--------|-----------|
| 小红书 | ✅     | ✅        | ✅    | ✅     | ✅      | ✅         |
| 抖音 | ✅     | ✅        | ✅    | ✅     | ✅      | ✅         |
| 快手 | ✅     | ✅        | ✅    | ✅     | ✅      |✅         |
| B 站 | ✅     | ✅        | ✅    | ✅     | ✅      | ✅         |
| 知乎 | ✅     | ✅        | ✅    | ✅     | ✅      |✅         |
| 微博 | ✅     | ✅        | ✅    | ✅     | ❌      | ✅         |
| 贴吧 | ✅     | ✅        | ✅    | ✅     | ❌       | ✅         |




## 获取Pro版本的访问权限
> 如果感兴趣可以加我微信，订阅Pro版本访问权限哦，有门槛💰。<br>
> 
> ⚠️⚠️仅针对想学习Pro版本源码实现的用户，如果是公司或者商业化盈利性质的就不要加我了，谢谢🙏 
> 
> 代码设计拓展性强，可以自己扩展更多的爬虫平台，更多的数据存储方式，相信对你架构这种爬虫代码有所帮助。

扫描下方我的个人微信，备注：pro版本（如果图片展示不出来，可以直接添加我的微信号：yzglan）
> 如果添加我微信显示频繁添加的话，可以尝试添加这个微信号：relakkes

<div style="max-width: 200px">  
<p><img alt="relakkes_wechat" src="../relakkes_weichat.JPG" style="width: 200px;height: 100%" ></p>
</div>

## Pro源代码仓库学习列表

- 🧹 **MediaCrawlerPro-Python**: 开源项目MediaCrawler的重构，移除playwright、增加多账号IP代理、代码优化.
- 🎯 **MediaCrawlerPro-SignSrv**: 爬虫JS签名逻辑单独抽出来作为最底层依赖服务.
- 🔗 **MediaCrawlerPro-Downloader**: 新开发的自媒体平台视频（图片）下载器，一个全栈项目，包含前端+后端+爬虫，适合学习全栈开发.
- 🛠️ **MediaCrawlerPro-Golang**: Golang语言版本，目前实现了最基本的xhs流程，开发中 .

### MediaCrawlerPro-Downloader视频下载器UI截图
> 前端：electorn + vue3 + ts + vite + elementui-plus。后端：Python+Tornado+Httpx+Pydantic
![img.png](img.png)
![img_1.png](img_1.png)

### MediaCrawlerPro中目录结构说明

<details>
<summary>🧹 <strong>MediaCrawlerPro-Python目录结构</strong></summary>

```tree
.
├── base                                                # 基础类目录
│   └── base_crawler.py                                 # 抽象类定义
├── cmd_arg                                             # 命令行参数目录
│   └── arg.py                                          # 命令行参数解析
├── config                                              # 配置文件目录
│   ├── README.md                                       # 配置文件说明
│   ├── accounts_cookies.xlsx                           # excel账号池模板
│   ├── base_config.py                                  # 基础配置
│   ├── db_config.py                                    # 数据库配置
│   ├── proxy_config.py                                 # 代理配置
│   └── sign_srv_config.py                              # 签名服务配置
├── constant                                            # 常量目录
│   ├── baidu_tieba.py                                  # 百度贴吧常量
│   ├── base_constant.py                                # 基础常量
│   ├── bilibili.py                                     # B站常量
│   ├── douyin.py                                       # 抖音常量
│   ├── kuaishou.py                                     # 快手常量
│   ├── weibo.py                                        # 微博常量
│   ├── xiaohongshu.py                                  # 小红书常量
│   └── zhihu.py                                        # 知乎常量
├── data                                                # 数据目录
├── docs                                                # 文档目录
├── media_platform                                      # 平台爬虫实现目录
│   ├── bilibili                                        # B站爬虫实现
│   │   ├── client.py                                   # B站客户端API
│   │   ├── core.py                                     # 主流程逻辑
│   │   ├── exception.py                                # 异常定义处理
│   │   ├── field.py                                    # 字段定义
│   │   └── help.py                                     # 辅助函数
│   ├── douyin                                          # 抖音爬虫实现
│   │   ├── client.py                                   # 抖音客户端API
│   │   ├── core.py                                     # 主流程逻辑
│   │   ├── exception.py                                # 异常定义处理
│   │   ├── field.py                                    # 字段定义
│   │   └── help.py                                     # 辅助函数
│   ├── kuaishou                                        # 快手爬虫实现
│   │   ├── graphql                                     # GraphQL查询目录
│   │   │   ├── comment_list.graphql                    # 评论列表查询
│   │   │   ├── search_query.graphql                    # 搜索查询
│   │   │   ├── video_detail.graphql                    # 视频详情查询
│   │   │   ├── vision_profile.graphql                  # 用户主页查询
│   │   │   ├── vision_profile_photo_list.graphql       # 图片列表查询
│   │   │   ├── vision_profile_user_list.graphql        # 用户列表查询
│   │   │   └── vision_sub_comment_list.graphql         # 子评论列表查询
│   │   ├── client.py                                   # 快手客户端API
│   │   ├── core.py                                     # 主流程逻辑
│   │   ├── exception.py                                # 异常定义处理
│   │   └── graphql.py                                  # GraphQL处理
│   ├── tieba                                           # 百度贴吧爬虫实现
│   │   ├── client.py                                   # 贴吧客户端API
│   │   ├── core.py                                     # 主流程逻辑
│   │   ├── field.py                                    # 字段定义
│   │   └── help.py                                     # 辅助函数
│   ├── weibo                                           # 微博爬虫实现
│   │   ├── client.py                                   # 微博客户端API
│   │   ├── core.py                                     # 主流程逻辑
│   │   ├── exception.py                                # 异常定义处理
│   │   ├── field.py                                    # 字段定义
│   │   └── help.py                                     # 辅助函数
│   ├── xhs                                             # 小红书爬虫实现
│   │   ├── client.py                                   # 小红书客户端API
│   │   ├── core.py                                     # 主流程逻辑
│   │   ├── exception.py                                # 异常定义处理
│   │   ├── extractor.py                                # 数据提取器
│   │   ├── field.py                                    # 字段定义
│   │   └── help.py                                     # 辅助函数
│   └── zhihu                                           # 知乎爬虫实现
│       ├── client.py                                   # 知乎客户端API
│       ├── core.py                                     # 主流程逻辑
│       ├── exception.py                                # 异常定义处理
│       ├── field.py                                    # 字段定义
│       └── help.py                                     # 辅助函数
├── model                                               # 数据模型目录
│   ├── m_baidu_tieba.py                                # 百度贴吧数据模型
│   ├── m_bilibili.py                                   # B站数据模型
│   ├── m_weibo.py                                      # 微博数据模型
│   ├── m_xiaohongshu.py                                # 小红书数据模型
│   └── m_zhihu.py                                      # 知乎数据模型
├── pkg                                                 # 项目包目录
│   ├── account_pool                                    # 账号池目录
│   │   ├── field.py                                    # 字段定义
│   │   └── pool.py                                     # 账号池实现
│   ├── cache                                           # 缓存目录
│   │   ├── abs_cache.py                                # 缓存抽象类
│   │   ├── cache_factory.py                            # 缓存工厂
│   │   ├── local_cache.py                              # 本地缓存
│   │   └── redis_cache.py                              # redis缓存
│   ├── proxy                                           # IP代理目录
│   │   ├── providers                                   # IP代理提供商目录
│   │   │   └── kuaidl_proxy.py                         # 快代理实现
│   │   ├── base_proxy.py                               # IP代理抽象类
│   │   ├── proxy_ip_pool.py                            # IP代理池实现
│   │   └── types.py                                    # IP代理类型定义
│   ├── rpc                                             # RPC目录
│   │   └── sign_srv_client                             # 签名服务客户端
│   │       ├── sign_client.py                          # 签名客户端实现
│   │       └── sign_model.py                           # 签名模型定义
│   ├── tools                                           # 工具目录
│   │   ├── crawler_util.py                             # 爬虫工具函数
│   │   ├── time_util.py                                # 时间工具函数
│   │   └── utils.py                                    # 通用工具函数
│   └── async_http_client.py                            # 异步HTTP客户端
├── repo                                                # 数据存储目录
│   ├── accounts_cookies                                # 账号池相关的存储
│   │   └── cookies_manage_sql.py                       # mysql账号池管理
│   └── platform_save_data                              # 平台数据存储
│       ├── bilibili                                    # B站数据存储
│       │   ├── bilibili_store_impl.py                  # B站存储实现
│       │   └── bilibili_store_sql.py                   # B站SQL定义
│       ├── douyin                                      # 抖音数据存储
│       │   ├── douyin_store_impl.py                    # 抖音存储实现
│       │   └── douyin_store_sql.py                     # 抖音SQL定义
│       ├── kuaishou                                    # 快手数据存储
│       │   ├── kuaishou_store_impl.py                  # 快手存储实现
│       │   └── kuaishou_store_sql.py                   # 快手SQL定义
│       ├── tieba                                       # 贴吧数据存储
│       │   ├── tieba_store_impl.py                     # 贴吧存储实现
│       │   └── tieba_store_sql.py                      # 贴吧SQL定义
│       ├── weibo                                       # 微博数据存储
│       │   ├── weibo_store_impl.py                     # 微博存储实现
│       │   └── weibo_store_sql.py                      # 微博SQL定义
│       ├── xhs                                         # 小红书数据存储
│       │   ├── xhs_store_impl.py                       # 小红书存储实现
│       │   └── xhs_store_sql.py                        # 小红书SQL定义
│       └── zhihu                                       # 知乎数据存储
│           ├── zhihu_store_impl.py                     # 知乎存储实现
│           └── zhihu_store_sql.py                      # 知乎SQL定义
├── schema                                              # 数据库表结构目录
│   ├── 2024082301_ddl.sql                              # 数据库变更脚本
│   ├── 2024082302_ddl.sql                              # 数据库变更脚本
│   ├── 2024082401_ddl.sql                              # 数据库变更脚本
│   ├── 2024091301_ddl.sql                              # 数据库变更脚本
│   ├── 2024101001_ddl.sql                              # 数据库变更脚本
│   ├── 2024112901_ddl.sql                              # 数据库变更脚本
│   └── tables.sql                                      # 基础表结构
├── static                                              # 静态文件目录
│   ├── img.png                                         # 图片资源
│   ├── img3.png                                        # 图片资源
│   ├── img4.png                                        # 图片资源
│   ├── img5.png                                        # 图片资源
│   ├── img6.png                                        # 图片资源
│   ├── img_1.png                                       # 图片资源
│   └── img_2.png                                       # 图片资源
├── test                                                # 单元测试目录
│   ├── test_expiring_local_cache.py                    # 本地缓存测试
│   ├── test_proxy_ip_pool.py                           # IP代理池测试
│   ├── test_redis_cache.py                             # redis缓存测试
│   └── test_utils.py                                   # 工具函数测试
├── Dockerfile                                          # Docker构建文件
├── LICENSE                                             # 开源协议
├── README.md                                           # 项目说明
├── async_db.py                                         # 异步数据库
├── db.py                                               # 数据库初始化
├── docker-compose.yaml                                 # docker-compose配置
├── main.py                                             # 程序入口
├── mypy.ini                                            # mypy配置
├── raw_directory_tree.txt                              # 目录结构文件
├── requirements.txt                                    # 项目依赖
└── var.py                                              # 上下文变量定义
```

</details>
<details>
<summary>🎯 <strong>MediaCrawlerPro-SignSrv目录结构</strong></summary>

```tree
.
├── apis                         # API接口目录
│   ├── base_handler.py          # Tornado Handler的基础类
│   ├── bilibili.py              # B站签名API接口
│   ├── douyin.py                # 抖音签名API接口
│   ├── xiaohongshu.py           # 小红书签名API接口
│   └── zhihu.py                 # 知乎签名API接口
├── constant                     # 常量定义目录
│   ├── base_constant.py         # 基础常量定义
│   └── error_code.py            # 错误代码定义
├── logic                        # 业务签名逻辑目录
│   ├── bilibili                 # B站签名业务逻辑
│   │   ├── bilibili_logic.py    # B站签名业务逻辑实现
│   │   └── help.py              # B站辅助函数
│   ├── douyin                   # 抖音签名业务逻辑
│   │   └── douyin_logic.py      # 抖音签名业务逻辑实现
│   ├── xhs                      # 小红书签名业务逻辑
│   │   ├── help.py              # 小红书辅助函数
│   │   └── xhs_logic.py         # 小红书签名业务逻辑实现
│   └── zhihu                    # 知乎签名业务逻辑
│       └── zhihu_logic.py       # 知乎签名业务逻辑实现
├── params                       # 参数定义目录
│   ├── base_model.py            # 基础参数模型
│   ├── bilibili_sign.py         # B站签名相关参数
│   ├── douyin_sign.py           # 抖音签名相关参数
│   ├── xiaohongshu_sign.py      # 小红书签名相关参数
│   └── zhihu_sign.py            # 知乎签名相关参数
├── pkg                          # 项目包目录
│   ├── cache                    # 缓存相关目录
│   │   ├── abs_cache.py         # 抽象缓存类
│   │   ├── cache_factory.py     # 缓存工厂类
│   │   └── local_cache.py       # 本地缓存实现
│   ├── custom_exceptions        # 自定义异常目录
│   │   └── base_exceptions.py   # 基础异常类
│   ├── js                       # JavaScript目录
│   │   ├── douyin.js            # 抖音相关JS文件
│   │   ├── stealth.min.js       # 去除浏览器自动化特征的JS
│   │   ├── xhs.js               # 小红书相关JS文件
│   │   └── zhihu.js             # 知乎相关JS文件
│   ├── playwright               # Playwright目录
│   │   ├── bilibili_manager.py  # B站Playwright管理器
│   │   ├── douyin_manager.py    # 抖音Playwright管理器
│   │   ├── manager.py           # 通用Playwright管理器
│   │   └── xhs_manager.py       # 小红书Playwright管理器
│   ├── utils                    # 工具函数目录
│   │   ├── base_utils.py        # 基础工具函数
│   │   └── crawler_util.py      # 爬虫工具函数
│   └── async_http_client.py     # 异步HTTP客户端
├── test                         # 测试目录
│   └── test_custom_getenv.py    # 自定义环境变量测试
├── Dockerfile                   # Docker配置文件
├── LICENSE                      # 开源协议
├── README.md                    # 项目说明文档
├── app.py                       # 应用程序入口
├── config.py                    # 配置文件
├── context_vars.py              # 上下文变量定义
├── img.png                      # 项目截图
├── project_tree.md              # 项目目录结构说明
├── requirements.txt             # 依赖项说明文件
└── urls.py                      # URL路由配置
```

</details>
<details>
<summary>🔗 <strong>MediaCrawlerPro-Downloader目录结构</strong></summary>

```tree
.                                                 # 项目根目录
├── DownloadServer                                # 下载服务端
│   ├── abs                                       # 抽象接口目录
│   │   └── abs_api_client.py                     # API客户端抽象类
│   ├── apis                                      # API接口目录
│   │   ├── base_handler.py                       # 基础处理器
│   │   ├── content_detail_handler.py             # 内容详情处理器
│   │   └── creator_query_handler.py              # 创作者查询处理器
│   ├── config                                    # 配置目录
│   │   └── base_config.py                        # 基础配置实现
│   ├── constant                                  # 常量目录
│   │   ├── base_constant.py                      # 基础常量定义
│   │   ├── bilibili.py                           # B站相关常量
│   │   ├── douyin.py                             # 抖音相关常量
│   │   ├── error_code.py                         # 错误码定义
│   │   ├── kuaishou.py                           # 快手相关常量
│   │   └── xiaohongshu.py                        # 小红书相关常量
│   ├── docs                                      # 文档目录
│   │   └── api                                   # API文档
│   │       └── swagger.yaml                      # Swagger接口文档
│   ├── logic                                     # 业务逻辑目录
│   │   ├── base_logic.py                         # 基础逻辑实现
│   │   ├── content_detail_logic.py               # 内容详情逻辑
│   │   └── creatory_query_logic.py               # 创作者查询逻辑
│   ├── logs                                      # 日志目录
│   │   ├── 2025-01-05.log                        # 日志文件
│   │   └── 2025-01-06.log                        # 日志文件
│   ├── models                                    # 数据模型目录
│   │   ├── base_model.py                         # 基础模型定义
│   │   ├── content_detail.py                     # 内容详情模型
│   │   └── creator.py                            # 创作者模型
│   ├── pkg                                       # 公共包目录
│   │   ├── cache                                 # 缓存模块
│   │   │   ├── abs_cache.py                      # 缓存抽象类
│   │   │   ├── cache_factory.py                  # 缓存工厂类
│   │   │   ├── local_cache.py                    # 本地缓存实现
│   │   │   └── redis_cache.py                    # Redis缓存实现
│   │   ├── custom_exceptions                     # 自定义异常目录
│   │   │   └── base_exceptions.py                # 基础异常定义
│   │   ├── media_platform_api                    # 媒体平台API目录
│   │   │   ├── bilibili                          # B站API实现
│   │   │   │   ├── client.py                     # B站客户端
│   │   │   │   ├── exception.py                  # B站异常定义
│   │   │   │   ├── extractor.py                  # B站数据提取器
│   │   │   │   └── field.py                      # B站字段定义
│   │   │   ├── douyin                            # 抖音API实现
│   │   │   │   ├── client.py                     # 抖音客户端
│   │   │   │   ├── extractor.py                  # 抖音数据提取器
│   │   │   │   └── help.py                       # 抖音帮助函数
│   │   │   ├── xhs                               # 小红书API实现
│   │   │   │   ├── client.py                     # 小红书客户端
│   │   │   │   ├── exception.py                  # 小红书异常定义
│   │   │   │   ├── extractor.py                  # 小红书数据提取器
│   │   │   │   ├── field.py                      # 小红书字段定义
│   │   │   │   └── help.py                       # 小红书帮助函数
│   │   │   └── media_platform_api.py             # 媒体平台API基类
│   │   ├── rpc                                   # RPC目录
│   │   │   └── sign_srv_client                   # 签名服务客户端
│   │   │       ├── sign_client.py                # 签名客户端实现
│   │   │       └── sign_model.py                 # 签名模型定义
│   │   ├── tools                                 # 工具目录
│   │   │   ├── crawler_util.py                   # 爬虫工具类
│   │   │   ├── time_util.py                      # 时间工具类
│   │   │   └── utils.py                          # 通用工具类
│   │   └── async_http_client.py                  # 异步HTTP客户端
│   ├── repo                                      # 数据仓库目录
│   ├── LICENSE                                   # 许可证文件
│   ├── README.md                                 # 说明文档
│   ├── app.py                                    # 应用入口
│   ├── context_vars.py                           # 上下文变量
│   ├── image.png                                 # 图片资源
│   ├── requirements.txt                          # 依赖清单
│   └── router.py                                 # 路由配置
├── DownloadUI                                    # 下载器UI项目
│   ├── build                                     # 构建目录
│   ├── scripts                                   # 脚本目录
│   │   ├── private                               # 私有脚本
│   │   │   └── tsc.js                            # TypeScript编译脚本
│   │   ├── build.js                              # 构建脚本
│   │   └── dev-server.js                         # 开发服务器脚本
│   ├── src                                       # 源码目录
│   │   ├── main                                  # 主进程目录（electron）
│   │   │   ├── static                            # 静态资源
│   │   │   ├── download-manager.ts               # 下载管理器
│   │   │   ├── main.ts                           # 主进程入口
│   │   │   ├── preload.ts                        # 预加载脚本
│   │   │   └── tsconfig.json                     # TS配置文件
│   │   └── renderer                              # 渲染进程目录（vue3 + element-plus）
│   │       ├── api                               # API目录
│   │       │   └── index.ts                      # API入口文件
│   │       ├── assets                            # 资源目录
│   │       │   ├── bilibili_icon.png             # B站图标
│   │       │   ├── douyin_icon.png               # 抖音图标
│   │       │   ├── github_icon.png               # GitHub图标
│   │       │   ├── kuaishou_icon.png             # 快手图标
│   │       │   ├── relakkes_weichat.jpg          # 微信二维码
│   │       │   ├── wechat_icon.png               # 微信图标
│   │       │   └── xiaohongshu_icon.png          # 小红书图标
│   │       ├── components                        # 组件目录
│   │       │   ├── ContactMe.vue                 # 联系我组件
│   │       │   ├── ContentList.vue               # 内容列表组件
│   │       │   ├── CreatorInfo.vue               # 创作者信息组件
│   │       │   ├── DownloadItem.vue              # 下载项组件
│   │       │   ├── Footer.vue                    # 页脚组件
│   │       │   └── Layout.vue                    # 布局组件
│   │       ├── public                            # 公共资源目录
│   │       │   ├── vite.svg                      # Vite图标
│   │       │   └── vue.svg                       # Vue图标
│   │       ├── typings                           # 类型定义目录
│   │       │   ├── content.d.ts                  # 内容类型定义
│   │       │   ├── creator.d.ts                  # 创作者类型定义
│   │       │   ├── download.d.ts                 # 下载类型定义
│   │       │   ├── electron-api.d.ts             # Electron API类型
│   │       │   ├── electron.d.ts                 # Electron类型
│   │       │   └── shims-vue.d.ts                # Vue类型定义
│   │       ├── utils                             # 工具目录
│   │       │   └── utils.ts                      # 工具函数
│   │       ├── App.vue                           # 根组件
│   │       ├── index.html                        # 入口HTML
│   │       ├── main.ts                           # 渲染进程入口
│   │       ├── style.css                         # 全局样式
│   │       └── tsconfig.json                     # TS配置文件
│   ├── LICENSE                                   # 许可证文件
│   ├── README.md                                 # 说明文档
│   ├── electron-builder.json                     # Electron打包配置
│   ├── package-lock.json                         # 包锁定文件
│   ├── package.json                              # 项目配置文件
│   ├── tsconfig.json                             # TS配置文件
│   └── vite.config.js                            # Vite配置文件
├── docs                                          # 文档目录
│   ├── image-2.png                               # 文档图片
│   └── image.png                                 # 文档图片
├── LICENSE                                       # 许可证文件
├── README.md                                     # 项目说明文档
└── project_tree.md                               # 项目目录结构说明
```

</details>
<details>
<summary>🛠 <strong>MediaCrawlerPro-Golang目录结构</strong></summary>

```tree
.
├── cmd                                               # 命令行工具目录
│   └── root.go                                       # 根命令实现
├── config                                            # 配置文件目录
│   ├── config.go                                     # 配置文件加载实现
│   ├── config.yml                                    # 配置文件
│   └── db_config.go                                  # 数据库配置实现
├── constant                                          # 常量定义目录
│   ├── account_pool.go                               # 账号池相关常量
│   ├── constant.go                                   # 通用常量定义
│   └── error_code.go                                 # 错误码定义
├── internal                                          # 内部代码目录
│   ├── models                                        # 数据模型目录
│   │   ├── xiaohongshu                               # 小红书相关模型
│   │   │   ├── common.go                             # 通用模型定义
│   │   │   ├── note_detail.go                        # 笔记详情模型
│   │   │   ├── search.go                             # 搜索相关模型
│   │   │   └── self_user.go                          # 用户信息模型
│   │   ├── account_pool.go                           # 账号池模型
│   │   └── ip_info.go                                # IP信息模型
│   ├── pkg                                           # 公共包目录
│   │   ├── account_pool                              # 账号池管理包
│   │   │   └── account_pool.go                       # 账号池实现
│   │   ├── cache                                     # 缓存包
│   │   │   ├── cache.go                              # 缓存接口定义
│   │   │   ├── local_cache.go                        # 本地缓存实现
│   │   │   └── redis_cache.go                        # Redis缓存实现
│   │   ├── httpclient                                # HTTP客户端包
│   │   │   ├── client.go                             # HTTP客户端实现
│   │   │   ├── client_test.go                        # 客户端测试
│   │   │   ├── config.go                             # 客户端配置
│   │   │   └── config_test.go                        # 配置测试
│   │   ├── proxy                                     # 代理管理包
│   │   │   ├── provider                              # 代理提供者目录
│   │   │   ├── base_proxy.go                         # 基础代理实现
│   │   │   └── ip_proxy.go                           # IP代理实现
│   │   ├── rpc                                       # RPC服务包
│   │   │   ├── sign                                  # 签名服务目录
│   │   │   └── signsrv                               # 签名服务实现
│   │   │       ├── client.go                         # 签名客户端
│   │   │       └── model.go                          # 签名模型
│   │   └── tools                                     # 工具包
│   │       ├── convert.go                            # 数据转换工具
│   │       ├── convert_test.go                       # 转换工具测试
│   │       ├── crawler.go                            # 爬虫工具实现
│   │       ├── crawler_test.go                       # 爬虫工具测试
│   │       ├── logger.go                             # 日志工具
│   │       └── time.go                               # 时间工具
│   ├── repo                                          # 数据仓库目录
│   │   ├── accounts_cookies                          # 账号Cookie管理
│   │   │   └── accounts_cookies.go                   # Cookie管理实现
│   │   ├── platform_save_data                        # 平台数据存储
│   │   │   └── xhs                                   # 小红书数据存储
│   │   │       ├── xhs_csv_repo.go                   # CSV存储实现
│   │   │       ├── xhs_db_repo.go                    # 数据库存储实现
│   │   │       ├── xhs_json_repo.go                  # JSON存储实现
│   │   │       ├── xhs_model.go                      # 存储模型定义
│   │   │       └── xhs_repo.go                       # 存储接口定义
│   │   └── db.go                                     # 数据库连接管理
│   ├── server                                        # 服务器目录
│   ├── service                                       # 业务服务目录
│   │   ├── xhs                                       # 小红书服务
│   │   │   ├── client.go                             # 小红书客户端
│   │   │   ├── convert.go                            # 数据转换实现
│   │   │   └── service.go                            # 服务实现
│   │   ├── client.go                                 # 通用客户端接口
│   │   └── service.go                                # 通用服务接口
│   └── app.go                                        # 应用程序入口
├── LICENSE                                           # 开源许可证
├── Makefile                                          # 项目构建文件
├── README.md                                         # 项目说明文档
├── go.mod                                            # Go模块定义
├── go.sum                                            # 依赖版本锁定
├── main.go                                           # 主程序入口
└── project_tree.md                                   # 项目结构说明
```
</details>

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
- [x] 账号池管理再次重构
- [x] 知乎支持爬取一个问答下的所有回答
- [x] MediaCrawlerPro-Downloader视频下载器开发完成
- [ ] MediaCrawlerPro-AI功能开发







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

