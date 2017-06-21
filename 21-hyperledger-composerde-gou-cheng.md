### Hyperledger Composer的构成

Hyperledger Composer是一个工具集，能够帮助开发人员进行基于Fabric的区块链应用开发。在经典的Fabric开发路线中，用户角色的描述和交易处理函数均在智能合约中实现，这使得智能合约十分庞杂。Composer将用户角色描述\(.cto\)和交易处理函数\(.js\)分开，并支持开发人员使用建模语言来描述用户角色。此外，Composer还支持访问权限控制\(.acl\)。

![](/assets/WX20170621-165852@2x.png)

上图[（图片出处）](https://hyperledger.github.io/composer/introduction/introduction.html)中所示的三个必要文件可以通过相应指令打包为.bna文件，即商业网络档案（？）文件。bna可以部署在运行中的fabric区块链网络上。Composer还提供了RESTful服务器生成方法、简单angular app生成方法。一个简单的、基于Composer的区块链应用开发流程可以参考下图。

![](/assets/WX20170621-170532@2x.png)

在接下来的章节中，我们将以[简单的物流信息跟踪系统](https://github.com/ztlbells/composer/tree/master/shipment-tracking-network)为例，描述如何构建一个基于Hyperledger Composer的应用。该应用的思路与实现与[官方示例-动物迁徙追踪系统](https://github.com/ztlbells/composer-sample-networks/tree/master/packages/animaltracking-network)大体一致。

