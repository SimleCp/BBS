# BBS

### Swift编写的iOS端和服务器端, 服务器端基于[Perfect](https://github.com/PerfectlySoft/Perfect)框架

iOS端地址: [https://github.com/zedxpp/BBS-iOS](https://github.com/zedxpp/BBS-iOS)

服务器端地址: [https://github.com/zedxpp/BBS-Server](https://github.com/zedxpp/BBS-Server)

![](https://github.com/SimleCp/BBS/blob/master/ScreenShot/1.png)

![](https://github.com/SimleCp/BBS/blob/master/ScreenShot/2.png)

![](https://github.com/SimleCp/BBS/blob/master/ScreenShot/3.png)

![](https://github.com/SimleCp/BBS/blob/master/ScreenShot/4.png)

注: 运行`BBS-iOS`, 如果你用的是我的服务器地址, 在帖子详情里面有很大的图片情况下, 加载的时候, 会卡一会, 服务器水管小. 没办法 T-T

### 已完成的接口

- [x] 注册
- [x] 登录
- [x] 所有帖子列表
- [x] 论坛列表
- [x] 帖子详情
- [x] 帖子评论列表
- [x] 评论帖子
- [x] 发布帖子
- [x] 上传图片
- [x] 获取当前用户信息
- [ ] ...

## 以下教程编译环境

#### Apple Swift version 4.0.3

查看方式, 打开终端, 输入`swift --version`

#### mysql  Ver 14.14 Distrib 5.7.19(mysql5.6版本也兼容)

输入`mysql --version`

## 使用方式

点个star不迷路 ^-^

#### 让iOS端跑起来

1. `clone` 和 `pod install`, 项目是基于`cocoapods`的.

2. 安装好后直接运行即可.

注: 

如果用这个地址, 需要把`BBS-Server`项目 `clone`到本地, 自己运行起来, 也就是`用你的mac当服务器`

```
let httpAdress = "http://0.0.0.0:8181/"
```

~~如果用这个地址, 直接运行`BBS-iOS`项目即可~~ `这个云服务器快到期了, 所以尽量结合 BBS-Server 项目查看iOS端的demo`
```
let httpAdress = "http://swift520.com:8181/"
```

配置文件在`BBS-iOS/Tool.swift`

#### 让服务端跑起来

1. `clone`项目, 并且`cd`到项目目录, `swift build`编译项目(如果你的终端没有翻墙, 那么这个过程会很慢)
2. 编译完成, 会出现`Linking ./.build/x86_64-apple-macosx10.10/debug/BBS-Server`这样的log输出. 直接拷贝`./.build/x86_64-apple-macosx10.10/debug/BBS-Server`, 运行即可.

过程如图:

![](https://github.com/SimleCp/BBS/blob/master/images/0.png)

3. 安装本地MySql, 请看此文章 [点我](http://zedxpp.com/2017/10/07/Swift%20Perfect%20Mac%E6%9C%AC%E5%9C%B0%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/)
只需要看安装部分即可, 安装完成后, 用命令启动数据库, 终端输出`Starting MySQL  . SUCCESS!`, 本地mysql服务启动完成.

4. 安装`Navicat Premium`的`Mac App`, 请自行网上搜索安装.

5. 用`Navicat Premium`, 新建`mysql`连接, 连接成功后, 打开数据库. 按下面的图, 新建一个`bbs`的数据库, 参数请务必和我图上的一致. 然后运行`bbs.sql`文件. 见下方图片.

![](https://github.com/SimleCp/BBS/blob/master/images/1.png)

![](https://github.com/SimleCp/BBS/blob/master/images/2.png)

![](https://github.com/SimleCp/BBS/blob/master/images/3.png)

![](https://github.com/SimleCp/BBS/blob/master/images/4.png)

![](https://github.com/SimleCp/BBS/blob/master/images/5.png)

6. 导入sql成功后, 在iOS端的`BBS-iOS/Tool.swift`切换为`let httpAdress = "http://0.0.0.0:8181/"`, 并且把`BBS-Server/Sources/BBS-Server/ServerConfiguration.swift`的数据库相关配置设置一下, 在没有更改端口号之类的情况下, 你需要填写你的数据库用户名和密码既可.

```
struct ServerConfiguration {
    let baseURL =  "http://localhost/" // 本地地址
    let name = "localhost"  
    let mysqlDBName  = "bbs"  // 数据库名
    let mysqlHost = "127.0.0.1" // 数据库本地地址
    let mysqlPort = 3306 // 默认端口号
    let mysqlPwd = "" // 数据库密码
    let mysqlUser = ""  // 数据库用户名
    let httpPort =  8181 // 服务器默认端口号
}
```

7. 重新运行`BBS-Server`和`BBS-iOS`项目. 现在, 服务器和数据库, 都是用的你mac上的了.


### 这两个小demo, 写了快两个月吧, 有很多细节地方没来得及完善, 同时写两端, 并且在不会用Perfect框架的情况下, 速度很慢了. 

### 如果你也想在mac或者服务器上部署一个属于自己的app后端, 请看我的Perfect框架使用系列文章, 戳我戳我[http://zedxpp.com](http://zedxpp.com)


