### 使用Land Registry

#### 单元测试

可先使用单元测试预览各个功能

```
node test
```

测试的命令有：

* node cli.js landregistry bootstrap
* node cli.js landregistry list
* node cli.js landregistry submit && node cli.js landregistry list

可以看出，主要测试的是（1）添加Asset、（2）显示Asset列表、（3）发送交易请求、（4）查看结果这四个功能

测试结果如下：![](/assets/import.png)![](/assets/submit&list.png)交易改变了Asset \#1148的状态，由ForSale=No转为Yes。

#### REST Server

可使用composer-rest-server启动一个基于Loopback的REST服务器，具体方法[见此](https://hyperledger.github.io/composer/integrating/getting-started-rest-api.html)。需要注意的是，如果使用的是v1.0.0版本的Fabirc，内置用户名和密码应为admin和adminpw。



#### 扩展阅读

[手把手教你如何从零创建一个Hyperledger Composer应用](https://hyperledger.github.io/composer/tutorials/developer-guide.html)  （文中虽然提及VSCode Editor，但这不是必要组件）

[Hyperledger Composer解决方案架构](https://hyperledger.github.io/composer/introduction/solution-architecture.html)

[术语表](https://hyperledger.github.io/composer/reference/glossary.html)





