### 使用modeling language描述用户角色

一个Hyperledger Composer CTO文件主要包含了命名空间、导入的声明和多种变量的声明。

用户角色描述示例可见[此处](https://github.com/ztlbells/composer-sample-networks/tree/master/packages/vehicle-lifecycle-network/models)，在文件**vehicle.cto**中，命名空间和声明导入方法如下：

> ```
> namespace org.acme.vehicle.lifecycle
>
>
> import composer.base.Person
>
> import composer.business.Business
> ```

需要声明的类有Assets, Events, Participants和Transactions。可以有抽象类和继承类。

以简单物流信息跟踪系统中的asset：物流中转站为例（[用户描述文件见此处](https://github.com/ztlbells/composer/blob/master/shipment-tracking-network/models/com.ibm.concerto.mozart.cto)）。

> ```
> asset Facility identified by facilityId {
>   o String facilityId
>   o String name
>   --> Shipment[] incomingShipments optional
>   --> PIC person_in_charge
> }
> ```

o后接类成员，--&gt;指向相关实例而非成员。此处incomingShipment代表一系列在途运件，故为array。

其余详解可见[官方教程](https://hyperledger.github.io/composer/reference/cto_language.html)。



