# 安装SharePoint 2016 {#concept_spr_fzt_2fb .task}

本文介绍如何安装SharePoint 2016的具体步骤。

使用本教程进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。

需要安装SharePoint 2016系统环境需要满足如下要求：

-   基础配置：
    -   Windows Server 2012
    -   4C 8G （请根据真实环境设计架构以及购买服务器配置）
-   软件环境：
    -   SQL server 2012 express
    -   SharePoint 2016
    -   AD
    -   DNS
    -   IIS
-   必备组件：Net Framework 3.5（安装SQL server 需要.net Framework 3.5 支持）

    **说明：** 

    -   安装Net Framework 3.5过程中，在**添加角色和功能**步骤可能会安装失败。如何解决，请参见[Windows Server 2012 R2或2016无法安装.NET Framework 3.5.1](https://www.alibabacloud.com/help/faq-detail/38203.htm)。
    -   SharePoint必备组件可以参见微软官方文档。安装SharePoint时会提示安装依赖组件，如果依赖组件安装失败，会导致SharePoint无法安装。

1.  搭建AD域。 

    **说明：** 客户端加域前请先修改SID，本教程只使用一台服务器来介绍如何安装SharePoint ，因此将所有角色和功能都安装在一台服务器上。在实际生产环境中，请勿将SQL Server、AD和SharePoint应用服务器搭建在一起。

2.  安装SQL Server 2012 Express。 SQL SERVER采用默认安装方式即可。本文中由于是测试环境，使用的是express版本，需要注意以下事项：

    **说明：** 

    -   express版本默认不支持tcp/ip协议，需要手动开启。
    -   express版本默认（可能）没有管理控制台，需要单独安装SQL管理工具。
    -   建议使用企业版数据库生成系统，express版本相对企业版本缺少部分功能。
3.  安装SharePoint 2016。 
    1.  安装SharePoint必备组件。 

        **说明：** 使用自动安装工具要求服务器具有访问外网的权限，如果访问不了，需要手动下载组件，然后使用命令安装，具体可以查看微软官方文档。

    2.  所有组件安装完成后，重启服务器，然后开始安装SharePoint。
    3.  运行SharePoint 2016安装向导，输入产品密钥，然后单击**继续**。 开始安装SharePoint 2016。
    4.  运行SharePoint配置向导。 
    5.  单击**创建新的服务器场**，然后单击**下一步**。
    6.  设置配置数据库信息和数据库访问帐户信息。 
    7.  指定服务器角色。 
    8.  指定SharePoint管理中心端口以及安全设置。 
    9.  完成配置向导并开始安装。 
    10. 配置成功，单击**完成**。 

安装完成后，您可以通过管理中心配置服务器场。配置服务器场时只开启您需要的服务，否则会造成不必要的内存开支。

