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

**\(第一次使用该实例应用，请先`npm install`，详细内容见1.3\)**



可以通过/packages/getting-started/scripts目录下的脚本来完成Fabric的初始化与启动（图来自[官方教程](https://hyperledger.github.io/composer/getting-started/development-tools.html)）。

![](https://hyperledger.github.io/composer/assets/img/developer-tools-commands.png)

先将所需镜像拖拽到本地

`./download-hyperledger.sh`

生成Fabric与Composer的连接文件

./`createProfile.sh`

启动Fabric（v1.0.0 ，包含一个orderer, 一个ca，两个peer）

`./start-hyperledger.sh`

成功完成启动的输出如下，粗体标出了较为重要的命令，便于定位错误源。

在这个脚本中，完成了下述事项：

docker-composer 在干净的环境中启动多个容器。（如何写docker-composer文件可以[参考此处](https://github.com/yeasy/docker-compose-files/tree/master/hyperledger)）

* CA 
* Orderer
* Peer0
* Peer1

sleep 15，等待启动过程

通过调用fabric node SDK及fabric-client相关函数创建channel（create-channel.js）

将节点加入channel（join-channel.js）

> \# Grab the current directorydirectory.
>
> DIR="$\( cd "$\( dirname "${BASH\_SOURCE\[0\]}" \)/.." && pwd \)"
>
> cd "$\( dirname "${BASH\_SOURCE\[0\]}" \)/.." && pwd
>
> dirname "${BASH\_SOURCE\[0\]}"
>
> \#
>
> cd "${DIR}"/hlfv1
>
> **docker-compose -f docker-compose.yml down              
> **
>
> Removing network hlfv1\_default
>
> docker rm $\(docker ps -aq\) &gt; /dev/null 2&gt;&1 \|\| true
>
> docker ps -aq
>
> **docker-compose -f docker-compose.yml up -d              
> **
>
> Creating network "hlfv1\_default" with the default driver
>
> Creating ca\_peerOrg1
>
> Creating orderer0
>
> Creating peer0
>
> Creating peer1
>
> \# wait for Hyperledger Fabric to start
>
> \# incase of errors when running later commands, increase this value and restart
>
> sleep 15
>
> **node create-channel.js              
> **
>
> info: Returning a new winston logger with default configurations
>
> using non-tls connection
>
> info: \[crypto\_ecdsa\_aes\]: This class requires a CryptoKeyStore to save keys, using the store: {"opts":{"path":"/home/ztluo/.hfc-key-store"}}
>
> info: \[Client.js\]: Successfully loaded user "admin" from local key value store
>
> Successfully loaded member from persistence
>
> Successfully enrolled user 'admin'
>
> Successfully read file
>
> Successfully created the channel.
>
> Successfully waited to make sure new channel was created.
>
> **node join-channel.js              
> **
>
> info: Returning a new winston logger with default configurations
>
> using non-tls connection
>
> Calling peers in organization "%s" to join the channel
>
> info: \[Peer.js\]: Peer.const - url: grpc://localhost:7051 options
>
> info: \[Peer.js\]: Peer.const - url: grpc://localhost:7056 options
>
> info: \[crypto\_ecdsa\_aes\]: This class requires a CryptoKeyStore to save keys, using the store: {"opts":{"path":"/home/ztluo/.hfc-key-store"}}
>
> info: \[Client.js\]: Successfully loaded user "admin" from local key value store
>
> Successfully loaded member from persistence
>
> Successfully enrolled user 'admin'
>
> info: \[join-channel\]: Join Channel R E S P O N S E : \[{"version":0,"timestamp":null,"response":{"status":200,"message":"","payload":{"type":"Buffer","data":\[\]}},"payload":{"type":"Buffer","data":\[\]},"endorsement":null},{"version":0,"timestamp":null,"response":{"status":200,"message":"","payload":{"type":"Buffer","data":\[\]}},"payload":{"type":"Buffer","data":\[\]},"endorsement":null}\]
>
> Successfully joined channel.
>
> Successfully joined peers in organization "peerOrg1" to the channel
>
> cd ../..



