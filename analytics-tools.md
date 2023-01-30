## 开源埋点系统调研


![](http://static.wozaizhao.com/test/posthog.png)

[PostHog](https://posthog.com/) [(github)](https://github.com/PostHog/posthog) 一个生产级网站流量分析工具，主要开发语言是TypeScript和Python。支持pg数据库，新手建议使用docker来一键部署，主要包含postgres,redis,chickhouse,zookeeper,kafka,web等，因我服务器配置不够（4核8G），一运行就卡死，直接试用了官方后端服务。功能比较强大，可以自定义Dashboard,Insights(关键指标)等，支持多种客户端，但没有小程序，可以在web客户端的基础上配适小程序。稍作修改后成功收到的事件消息，但里面的用户标识全是uuid，如果要用可能要改为openid或手机号。
综上，PostHog是一款强大的流量分析工具，建议使用，但是服务端如果不用docker布署，会有相当的运维工作。另客户端脚本要配适小程序，有一点点工作量。

![](http://static.wozaizhao.com/test/umami.png)

[umami](https://umami.is/) [(github)](https://github.com/umami-software/umami) 一个轻量级网站分析工具，使用js编写，支持postgresql和mysql，客户端只有web用的js，小程序使用要配适一下。
综上，功能比较简单，胜在轻量，如果对功能要求不高，可以使用。后期如要加功能，需二次开发。如遇并发性能问题，需自行加消息队列等。


**自研** 使用java语言编写服务，数据存储使用pg数据库或Elasticsearch。前端无开发量，使用原有接口。
此方案，要有后端资源，前端基本不用开发。
