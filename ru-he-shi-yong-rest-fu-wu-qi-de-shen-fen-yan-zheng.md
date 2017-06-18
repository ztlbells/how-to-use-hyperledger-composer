### 如何使用REST服务器的身份验证

官方教程其实已经给出了比较完备的身份验证服务配置[教程](https://hyperledger.github.io/composer/integrating/enabling-rest-authentication.html)，但如果不采用GIthub的OAuth转而采用Fabric当中内置的身份，则需要用到Fabric-CA来issue新身份，获取enrollSecret。

如何使用Fabric-CA可以见[官方教程](https://hyperledger-fabric-ca.readthedocs.io/en/latest/users-guide.html#getting-started)，这里主要记录：

（1）基于Land Registry的docker-compose构建的Fabric网络来创建新身份

（2）完成基于Blockchain Identity的REST服务器身份验证

1.登入Fabric-CA的docker image （container ID 可以通过`docker ps`查看）

`docker exec -it <container ID> bash`

2.通过docker-compose.yml可以看到，FABRIC\_CA\_HOME被设置为/etc/hyperledger/fabric-ca-server，故登入container的该路径中进行fabric CA的相关操作。可以先用内置admin来init一下试试手。

`root@cb2a73e1b798:/etc/hyperledger/fabric-ca-server# fabric-ca-server init -b admin:adminpw`

> 2017/06/10 08:34:51 \[INFO\] Configuration file location: /etc/hyperledger/fabric-ca-server/fabric-ca-server-config.yaml
>
> 2017/06/10 08:34:51 Initialize BCCSP \[SW\]
>
> 2017/06/10 08:34:51 \[INFO\] The CA key and certificate files already exist
>
> 2017/06/10 08:34:51 \[INFO\] Key file location: /etc/hyperledger/fabric-ca-server/ca-key.pem
>
> 2017/06/10 08:34:51 \[INFO\] Certificate file location: /etc/hyperledger/fabric-ca-server/ca-cert.pem
>
> 2017/06/10 08:34:51 \[INFO\] Initialized sqlite3 data base at /etc/hyperledger/fabric-ca-server/fabric-ca-server.db
>
> 2017/06/10 08:34:51 \[INFO\] Initialization was successful

3.该路径下的文件如下所示

`root@cb2a73e1b798:/etc/hyperledger/fabric-ca-server# ls`

> ca-cert.pem  ca-key.pem  fabric-ca-server-config.yaml  fabric-ca-server.db

fabric-ca-server.db内的数据来保存了身份注册情况。

* 采用命令`fabric-ca-client enroll -u http://user:userpw@serverAddr:serverPort`配置enrollment相关信息 

这里可以使用`fabric-ca-client enroll -u http://admin:adminpw@localhost:7054`

* 注册新enrollID，返回enrollSecret

`root@cb2a73e1b798:/etc/hyperledger/fabric-ca-server# fabric-ca-client register --id.name admin2 --id.type user --id.affiliation org1.department1`

> 2017/06/10 08:50:43 \[INFO\] User provided config file: /etc/hyperledger/fabric-ca-server/fabric-ca-client-config.yaml
>
> 2017/06/10 08:50:43 Initialize BCCSP \[SW\]
>
> 2017/06/10 08:50:43 \[INFO\] Configuration file location: /etc/hyperledger/fabric-ca-server/fabric-ca-client-config.yaml
>
> **Password: wWwUqTKeNuDx**

* 保存enrollID和enrollSecret，将相应账号密码对加入到官方教程给出的default wallet中。（详见[Adding a Blockchain identity to the default wallet](https://hyperledger.github.io/composer/integrating/enabling-rest-authentication.html)）



