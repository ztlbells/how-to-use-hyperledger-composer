### .bna文件的使用方法

首先确保composer-cli的npm模块已经安装

```
npm install -g composer-cli
```

#### 

#### 生成.bna文件

创建一个business network archive，configuration写在项目根目录下的**package.json**中

```
composer archive create -a <business-network-archive>
或者
composer archive create --sourceType dir --sourceName .
```

查看现有的business network archive中的内容

```
composer archive list -a <business-network-archive>
```

#### 

#### 部署.bna

详细使用方法[见此](https://hyperledger.github.io/composer/reference/composer.network.deploy.html)，假如要部署shipment-tracking-network，命令则为

```
composer network deploy -a shipment-tracking-network@0.0.1.bna -i admin -s adminpw -p hlfv1
```

参数解释：

```
  --archiveFile, -a              bna文件名，可能含有版本号 [必需]
  --connectionProfileName, -p    链接文件名，如果是fabric1.0，则对应hlfv1 [默认0.6]
  --enrollId, -i                 登录fabric的账号，fabric1.0默认为admin [必需]
  --enrollSecret, -s             登录fabric的密码，admin对应adminpw [必需]

  * 如果使用fabric 0.6，内置账号密码对为-i WebAppAdmin -s DJY27pEnl16d
```

成功部署的截图如下![](/assets/WX20170621-230627@2x.png)

在此基础上可[启用RESTful服务器。](https://hyperledger.github.io/composer/integrating/integrating-index.html)

![](/assets/WX20170602-231844@2x.png)

也可以进行[node.js应用的开发](https://hyperledger.github.io/composer/applications/node.html)，或者使用`yo hyperledger-composer`生成骨架Angular项目。



