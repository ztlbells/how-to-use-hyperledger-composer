### 交易处理函数

在物流信息追踪系统中，假设一个运件有如下三个状态：

```
enum ShipmentStatus {
    o IN_STATION
    o IN_TRANSIT
    o SIGNED_FOR
}
```

若一个工作站成员想要更新物流信息（e.g. 运件状态：IN\_TRANSIT -&gt; IN\_STATION），则需要发送一条**交易**来修改运件状态。

需要注意的是，一个交易处理函数对应用户描述文件中的一条交易，需要在@param中标记出来。

```js
/**
* @param {com.biz.ShipmentDepart} shipmentDepart
* @transaction
*/
```

交易处理函数的核心是使用composer-runtime的promise：[getAssetRegistry\(id\)](https://hyperledger.github.io/composer/jsdoc/module-composer-runtime.html#getAssetRegistry__anchor)，具体用法可参考[该例子](https://github.com/ztlbells/composer/blob/master/shipment-tracking-network/lib/mozart.cto.js)。



