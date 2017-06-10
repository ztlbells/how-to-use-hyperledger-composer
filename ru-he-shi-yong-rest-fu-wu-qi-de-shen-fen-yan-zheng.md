### 如何使用REST服务器的身份验证

官方教程其实已经给出了比较完备的身份验证服务配置[教程](https://hyperledger.github.io/composer/integrating/enabling-rest-authentication.html)，但如果不采用GIthub的OAuth转而采用Fabric当中内置的身份，则需要用到Fabric-CA来issue新身份，获取enrollSecret。



如何使用Fabric-CA可以见[官方教程](https://hyperledger-fabric-ca.readthedocs.io/en/latest/users-guide.html#getting-started)，这里主要记录：

（1）基于Land Registry的docker-compose构建的Fabric网络来创建新身份

（2）完成基于Blockchain Identity的REST服务器身份验证



1.登入Fabric-CA的docker image （container ID 可以通过`docker ps`查看）

`docker exec -it <container ID> bash`



2.通过docker-compose.yml可以看到，FABRIC\_CA\_HOME被设置为/etc/hyperledger/fabric-ca-server，故登入container的该路径中进行fabric CA的相关操作。

`root@cb2a73e1b798:/etc/hyperledger/fabric-ca-server# fabric-ca-server init -b admin:adminpw`





