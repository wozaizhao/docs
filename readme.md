

### 我在找是什么
wozaizhao.com是我很久以前注册的一个域名，后来也相继注册了我在找公众号，我在找小程序。都是用来做一些实验性质的项目。

### 为什么有这个项目
这个项目就是一个**模版**，当我们开始一个移动端网页应用或小程序项目时，可能要做一些技术选型、框架搭建、登录注册上传功能等前期工作，这个项目是想让你跳过这些步骤，直接进入到业务开发阶段。
这个模版分三个子项目：h5端、小程序端、后端；技术栈分别是vue3，小程序原生开发，go语言。
也希望通过这个项目，可以结交一些朋友。

### 适用场景
这个项目在有些时候可以给你节省不少时间，比如你的项目也想用以下这些技术来实现：
- vue
- vant
- 小程序登录
- jweixin.js在vue3中使用
- mysql
- go语言写后端等等

### 功能
- 极验滑块验证
    > 获取手机验证码时，使用了极验的人机验证
- 使用手机号及验证码登录
    > 使用小程序登录时，会记录openID，下次打开小程序自动使用openID登录
- 使用小程序openID快捷登录
    > 小程序或h5使用openID快捷登录
- 小程序登录code2Session接口
    > 使用本接口，来得到openID
- 公众号GetConfig接口
    > 使用本接口，获取公众号配置，然后可以使用jssdk功能
- 小程序滑块验证接口
    > 腾讯官方提供的小程序人机验证插件后端接口实现
- 获取当前用户
    > 根据token获取当前登录的用户信息
- 更新用户信息（头像、昵称、性别、简介等）
    > 更新用户的各项信息
- 上传
    > 上传文件，当前仅用来更新头像，使用七牛云存储图片及cdn功能
- 短信验证码
    > 使用阿里云通信服务发送短信验证码

### 技术特点
- **代码检查及格式化**
    > h5及小程序使用eslint检查代码，使用prettier格式化代码；go自带代码检查及格式化。
- **Github Actions 自动化部署**
    > 提交代码即自动部署
- **vue3+vite**
    > 使用vue3及vite来构建h5端
- vant+**tailwind**
    > h5端使用vant组件库，同时搭配tailwind辅助，基本不需要写css。
- jweixin
    > h5端在微信中打开时，通过jssdk使用公众号接口
- 在小程序中使用async await
    > 使用async await使代码逻辑更合理清晰
- jwt
    > 使用jwt token鉴权
- **https**
    > 使用接口及资源使用https，全为免费方案：阿里云免费证书及letsencrypt服务

### H5端

![](https://img.wozaizhao.com/screen/h5-login.jpg) 登录
![](https://img.wozaizhao.com/screen/h5-geetest.jpg) 滑块验证

![](https://img.wozaizhao.com/screen/h5-login-submit.jpg) 登录提交
![](https://img.wozaizhao.com/screen/h5-me.jpg) 我的
![](https://img.wozaizhao.com/screen/h5-profile.jpg) 个人信息
![](https://img.wozaizhao.com/screen/h5-update.jpg) 更新


### 小程序端

![](https://img.wozaizhao.com/screen/weapp-login.jpg) 登录
![](https://img.wozaizhao.com/screen/weapp-me.jpg) 我的
![](https://img.wozaizhao.com/screen/webview-me.jpg) webview 我的

小程序界面基本同h5端一样，先写的h5端，然后移植为小程序代码，tailwind直接复制h5端生成的少量tailwind css代码。

### 服务端
主要使用以下库
- [github.com/alibabacloud-go/dysmsapi-20170525/v2](github.com/alibabacloud-go/dysmsapi-20170525/v2) 阿里云通信sdk
- [github.com/gin-gonic/gin](github.com/gin-gonic/gin) 流行的go web框架
- [github.com/golang-jwt/jwt](github.com/golang-jwt/jwt) jwt 
- [github.com/qiniu/go-sdk/v7](github.com/qiniu/go-sdk/v7) 七牛云sdk
- [github.com/silenceper/wechat/v2](github.com/silenceper/wechat/v2) 微信sdk
- [github.com/sirupsen/logrus](github.com/sirupsen/logrus) 日志
- [gorm.io/gorm](gorm.io/gorm) orm库，操作mysl

### 第三方服务

- [letsencrypt](https://letsencrypt.org/) 免费证书服务，支持泛域名
- [极验](https://geetest.com) 滑块验证码服务商，在项目中用来做发短信的人机认证
- [腾讯验证码](https://mp.weixin.qq.com/wxopen/plugindevdoc?appid=wx3acdde82f7cf0e6e&token=&lang=zh_CN) 腾讯官方提供的验证码组件
- [阿里云](https://aliyun.com/) 云服务商，项目的前后端都布署在阿里云服务器上，数据库是跑云服务器的docker中，同时项目的短信服务、域名等用的也是阿里云的
- [七牛云](https://www.qiniu.com/) 云计算及数据服务提供商，项目中的存储，主要是图片存储用的是七牛云

### 欢迎与我联系 [https://github.com/xchao0213](https://github.com/xchao0213) wechat id: beetle2013