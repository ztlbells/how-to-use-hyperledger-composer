### 启动一个简单的应用：Land Registry

本应用基于官方提供的示例

`git clone https://github.com/hyperledger/composer-sample-applications-hlfv1.git`

回到/packages/getting-started，进行应用的快速启动

```
node install
```

查看可用命令

```
node run
```

> Lifecycle scripts included in getting-started:
>
> preinstall
>
> ```
> composer --version \|\| { echo 'Please first run npm install -g composer-cli' ; exit 1;}
> ```
>
> test
>
> ```
> mocha --recursive && npm run bootstrapAssets && npm run listAssets && npm run submitTransaction
> ```
>
> postinstall
>
> ```
> scripts/download-hyperledger.sh && scripts/createProfile.sh && npm run startHLF && npm run deployNetwork
> ```
>
> available via \`npm run-script\`:
>
> submitTransaction
>
> ```
> node cli.js landregistry submit && node cli.js landregistry list
> ```
>
> listAssets
>
> ```
> node cli.js landregistry list
> ```
>
> bootstrapAssets
>
> ```
> node cli.js landregistry bootstrap
> ```
>
> startHLF
>
> ```
> scripts/start-hyperledger.sh
> ```
>
> stopHLF
>
> ```
> scripts/stop-hyperledger.sh
> ```
>
> teardownHLF
>
> ```
> scripts/teardown.sh
> ```
>
> deployNetwork
>
> ```
> composer archive create --sourceName digitalproperty-network --sourceType module --archiveFile digitalPropertyNetwork.bna && composer network deploy --archiveFile digitalPropertyNetwork.bna  -p hlfv1 -i admin -s adminpw && composer network list -n digitalproperty-network -p hlfv1 -i admin -s adminpw
> ```

如果你跳过了快速安装部分，则需要运行下述命令来完成镜像拖拽、链接文件生产和fabric启动工作。

```
scripts/download-hyperledger.sh && scripts/createProfile.sh && scripts/start-hyperledger.sh
```

鉴于我们已经完成了Fabric镜像的拖拽和启动，现在只需要部署BNA（Business Network Archive）到Fabric上。

使用组合命令

```
composer archive create --sourceName digitalproperty-network --sourceType module --archiveFile digitalPropertyNetwork.bna && composer network deploy --archiveFile digitalPropertyNetwork.bna  -p hlfv1 -i admin -s adminpw && composer network list -n digitalproperty-network -p hlfv1 -i admin -s adminpw
```

上述命令将完成三件事：

* 生成.bna文件
* 部署.bna文件（应用网络）
* 查看已部署的应用网络

如无差错，应有如下输出：

> **Creating Business Network Archive        
> **
>
> Node module search path :
>
> undefined
>
> Not found in main node\_module search path, trying current directory :/github.com/composer-sample-applications-hlfv1/packages/getting-started/node\_modules/digitalproperty-network
>
> Looking for package.json of Business Network Definition in /github.com/composer-sample-applications-hlfv1/packages/getting-started/node\_modules/digitalproperty-network
>
> Found:
>
> Description:Digital Property Network
>
> Name:digitalproperty-network
>
> Identifier:digitalproperty-network@0.0.7
>
> Written Business Network Definition Archive file to digitalPropertyNetwork.bna
>
> Command completed successfully.
>
> **Command succeeded        
> **
>
> **Deploying business network from archive**: digitalPropertyNetwork.bna
>
> **Business network definition**:
>
> ```
> Identifier: digitalproperty-network@0.0.7
>
> Description: Digital Property Network
> ```
>
> ✔ Deploying business network definition. This may take a minute...
>
> **Command succeeded        
> **
>
> ✔** List business network digitalproperty-network        
> **
>
> **name:**       digitalproperty-network
>
> **models:**
>
> * net.biz.digitalPropertyNetwork
>
> **scripts:         
> **
>
> * lib/DigitalLandTitle.js
>
> **registries:         
> **
>
> net.biz.digitalPropertyNetwork.LandTitle:
>
> ```
> id:           net.biz.digitalPropertyNetwork.LandTitle
>
> name:         Asset registry for net.biz.digitalPropertyNetwork.LandTitle
>
> registryType: Asset
> ```
>
> net.biz.digitalPropertyNetwork.SalesAgreement:
>
> ```
> id:           net.biz.digitalPropertyNetwork.SalesAgreement
>
> name:         Asset registry for net.biz.digitalPropertyNetwork.SalesAgreement
>
> registryType: Asset
> ```
>
> **Command succeeded        
> **



