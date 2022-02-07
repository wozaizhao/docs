## 部署

### 先决条件
- 如果在线上布署h5端，你需要一个域名，**要花钱**购买一个。推荐阿里云。
- 如果要有小程序端，你需要注册一个小程序，免费。如果你要使用webview等功能，需要以企业身份注册小程序。
- 如果要在h5中使用微信jssdk，你需要注册一个公众号，免费。
- 在开发阶段，可以在本地电脑上运行后端，但如果你要布署后端，你需要一台服务器，**要花钱**购买。推荐阿里云。
- 如果需要极验的人机验证，你需要注册一个极验帐号，记得使用国际版（英文版）则免费。
- 如果需要七牛云存储服务，你需要注册一个七牛云帐号，免费（每月免费存储和流量足够用了）。
- https证书，可以使用云厂商的免费证书或letsencrypt

基本上就域名和服务器要钱，域名一年60左右。服务器可以看看云服务厂商的活动，一般新用户价钱是不贵的。这里推荐阿里云，只是个人偏好，使用任何云服务都是可以的，国内的腾讯云、华为云等等，甚至包括aws、Microsoft Azure等（使用银行卡注册，成功后可以免费使用一年云主机，缺点是服务器在境外，有点慢）

### h5端布署
- 下载项目或git clone项目到本地
- yarn 或 npm install
- npm run build
- 将dist目录复制到服务器
- 配置域名指向

- 配置nginx
    参见app.conf,img.conf

- github actions secrets

    - REMOTE_TARGET 服务器上h5目录，比如/data/www/xxx
    - REMOTE_HOST 服务器ip地址
    - REMOTE_PORT 服务器ssh端口
    - REMOTE_USER 服务器ssh用户名
    - SERVER_SSH_KEY 服务器ssh私钥

### 小程序布署
- 下载项目或git clone项目到本地
- npm install
- 在小程序开发工具中，构建npm
- 在小程序后台，配置h5域名为业务域名，配置后端域名为request域名
- 使用你的小程序id,上传并查看小程序

### mysql redis
推荐使用docker来运行mysql和redis，避免了繁琐的配置
```
// 安装mysql
docker run --name mysql8 -e MYSQL_ROOT_PASSWORD=your password -p 3306:3306 -d mysql:8

// 安装redis
docker run --name redis -d redis
```

### 后端布署 
因为我的服务器上已经有一个叫api的后端服务，所以这个项目的后端我起了个另外的名字gate，一般命名为api
- 安装go环境
- 下载项目或git clone项目到本地
- 配置nginx
    参见gate.conf
- 在mysql创建数据库    
- 配置config.yarm 参见config.yaml.default
- 在项目目录运行 go run main.go
- 推荐以服务的方式布署后端应用
    在 /etc/systemed/system 增加service文件，参见gate.service
- github actions secrets
    除REMOTE_TARGET外同h5，REMOTE_TARGET为可执行文件目录
