# 安装与开发环境的配置

### 环境配置

目前Hyperledger Composer支持Ubuntu Linux 14.04 / 16.04 LTS \(64-bit\), Mac OS 10.12。经测试，Debian 8.x亦支持。

依赖项如下所示：

* Docker Engine:  17.03 +
* Docker-Compose: 1.8 +
* Node: 6.x （注意：7.x+目前还不支持）
* npm: 3.10.x
* git: 2.9.x

如果你使用的是Ubuntu，那么恭喜，你可以直接使用官方提供的bash文件自动完成上述依赖项的安装。如不能使用脚本安装，则需通过手动方法完成相应安装。

如使用脚本安装，你可以使用curl将该脚本文件下载下来：

`curl -O https://raw.githubusercontent.com/hyperledger/composer-sample-applications/master/packages/getting-started/scripts/prereqs-ubuntu.sh`

修改权限：

`chmod u+x prereqs-ubuntu.sh`

运行脚本文件：

`./prereqs-ubuntu.sh`

墙内用户可能会碰到docker engine无法成功安装的问题，这里推荐[Docker——从入门到实践](https://yeasy.gitbooks.io/docker_practice/content/install/ubuntu.html)中提到的安装方法，如：

阿里云的安装脚本

`curl -sSL http://acs-public-mirror.oss-cn-hangzhou.aliyuncs.com/docker-engine/internet | sh -`

### 快速安装

安装composer命令行包

`npm install -g composer-cli`

安装REST服务器生成包

`npm install -g composer-rest-server`

如希望搭建应用，可以使用yeoman及composer应用框架生产包：

`npm install -g yo`

`npm install -g composer-rest-server`



快速搭建一个示例应用可以选择

`git clone https://github.com/hyperledger/composer-sample-applications-hlfv1.git`

通过/packages/getting-started/scripts目录下的脚本来完成Fabric的初始化与启动（图来自[官方教程](https://hyperledger.github.io/composer/getting-started/development-tools.html)）。

![](https://hyperledger.github.io/composer/assets/img/developer-tools-commands.png)

先将所需镜像拖拽到本地

`./download-hyperledger.sh`

生成Fabric与Composer的连接文件

./`createProfile.sh`

启动Fabric（v1.0.0 ，包含一个orderer, 一个ca，两个peer）

`./start-hyperledger.sh`



### 启动一个简单的应用：Land Registry

回到/packages/getting-started，进行应用的快速启动

`npm install`

完成单元测试

`npm test`





