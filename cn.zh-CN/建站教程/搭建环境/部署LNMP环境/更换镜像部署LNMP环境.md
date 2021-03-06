# 更换镜像部署LNMP环境

LNMP分别代表Linux、Nginx、MySQL、PHP。本文介绍为已购ECS实例更换镜像，以部署LNMP环境的操作步骤。

-   已注册阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm?)。
-   已在实例安全组的入方向添加规则并放行80端口。 若尚未添加规则，请先[添加安全组规则](/cn.zh-CN/安全/安全组/添加安全组规则.md)。

    |规则方向|授权策略|协议类型|端口范围|优先级|授权类型|授权对象|
    |----|----|----|----|---|----|----|
    |入方向|允许|自定义TCP|80/80|1|IPv4地址段访问|允许访问实例LNMP服务的客户端公网IP地址，多个IP之间用逗号隔开。 允许所有IP访问时，授权对象为0.0.0.0/0。 |


您可选用以下几种方式在ECS实例上部署LNMP环境：

-   [镜像部署LNMP环境](#step_92i_e0z_xeq)
-   [ROS部署LNMP环境](/cn.zh-CN/建站教程/搭建环境/部署LNMP环境/使用ROS部署LNMP环境.md)
-   [手动部署LNMP环境](/cn.zh-CN/建站教程/搭建环境/部署LNMP环境/手动部署LNMP环境（CentOS 7）.md)

镜像部署和手动部署方式的对比如下表所示。

|对比项|镜像部署|手动部署|
|:--|:---|:---|
|部署所需时间|3-5分钟，快速部署上云|1-2天。选择适合的操作系统、中间件、数据库、各类软件、插件、脚本，再进行安装和配置|
|专业性 IOPS|由运维过万级用户的优质服务商提供|依赖开发人员的开发水平|
|个性化|支持主流应用场景|可满足个性化的部署要求|
|安全性|经过严格安全审核，集成最稳定安全的版本|依赖开发人员的开发水平|
|售后服务|专业售后工程师团队支持|依赖运维人员的经验，或由外包团队支持|

如需个性化定制部署LNMP环境，建议您使用手动部署。如需快速、方便地部署LNMP环境，推荐您使用镜像部署。阿里云的[云市场](http://market.aliyun.com/)提供了丰富的镜像资源，集成了操作系统和应用程序。在创建实例时，选择包含了LNMP环境的镜像，创建后就无需再部署环境。使用LNMP环境云市场镜像的方式如下：

-   创建ECS实例时，直接选择包含LNMP环境的云市场镜像。
-   创建ECS实例后，通过更换操作系统的方式，将已购实例的操作系统更换为包含LNMP环境的镜像。

本教程的操作步骤适用于第二种方式，即已创建ECS实例，但希望通过更换镜像来快速部署LNMP环境的场景。本教程介绍镜像部署的通用操作步骤。不同云市场镜像的具体部署方法，请阅读镜像产品说明或与镜像供应商联系获取。

**说明：**

-   云服务器ECS不支持虚拟化软件（如KVM、Xen、VMware等）的安装部署。
-   更换操作系统后，原系统盘会被释放，数据将丢失且无法找回。请您操作前详细了解相关操作说明，详情请参见[更换系统盘（非公共镜像）](/cn.zh-CN/块存储/云盘基础操作/更换系统盘/更换系统盘（非公共镜像）.md)。
-   更换操作系统时，ECS实例数据盘的数据不会受到影响。因此建议您将系统盘的个人数据备份到数据盘中，或采用其他方式进行备份。
-   更换操作系统后，ECS实例的IP地址不会改变。

1.  登录[ECS管理控制台](https://ecs.console.aliyun.com)。

2.  在左侧导航栏，单击**实例与镜像** \> **实例**。

3.  在实例列表页面，选中目标实例，单击实例ID或**操作**列的**管理**。

    ![实例列表](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9802649951/p102136.png)

4.  停止目标实例。

    **说明：** 停止实例会影响您的业务，请谨慎操作。

    1.  在实例详情页面，单击**停止**。

        ![实例详情](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6608773061/p102137.png)

    2.  在停止实例对话框，选择**停止方式**和**停止模式**，然后单击**确定**。

        **说明：** 如果您停止实例是为了更换系统盘、重新初始化磁盘、更改实例规格、修改私网IP等操作，建议您选中**停止后仍旧保留实例并继续收费**选项，避免实例启动失败。

        ![停止实例](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9802649951/p102138.png)

5.  更换ECS实例系统盘。

    1.  在实例详情页面的**基本信息**区域，单击**更换操作系统**。

        ![更换操作系统](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6608773061/p102139.png)

    2.  在更换系统盘对话框，单击**确定，更换操作系统**。

        ![更换系统盘须知](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1112649951/p14398.png)

    3.  在**镜像类型**区域，单击**镜像市场**，然后单击**从镜像市场选择（含操作系统）**。

        ![选择镜像](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0902649951/p21021.png)

    4.  在左侧导航栏，选择镜像分类，或者在搜索栏中输入LNMP，然后单击**搜索**。选中目标镜像后，单击**使用**。

        您需要单击对应镜像的标题名称，跳转至镜像售卖页，以获取镜像的使用说明。

        ![镜像市场选择镜像](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0902649951/p102140.png)

    5.  设置ECS实例的登录密码。在**登录密码**文本框中输入密码，并在**确认密码**文本框中再次输入密码。

    6.  在更换操作系统页面右下角， 选中**《云服务器ECS服务条款》**和**《镜像商品使用条款》**并单击**确定更换**。

        ![确定更换](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0902649951/p21043.png)


出现系统盘更换成功对话框时，表明您已成功使用镜像市场的镜像更换ECS实例的操作系统。单击**返回实例列表**返回实例列表页面。启动并登录ECS实例后，即可使用实例的LNMP环境。

![系统盘更换成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1112649951/p21046.png)

