---
title: "Management Authorization Rules Scope &lt;scope&gt;"
author: rick-anderson
description: "Overview The &lt;scope&gt; element of the &lt;authorizationRules&gt; element specifies the virtual path of the site or application to which remote IIS Manage..."
ms.date: 09/26/2016
ms.assetid: c1f0d444-5d46-4e41-8d90-45834ae8b677
msc.legacyurl: /configreference/system.webserver/management/authorization/authorizationrules/scope
msc.type: config
ms.custom: sfi-image-nochange
---
# Management Authorization Rules Scope &lt;scope&gt;

<a id="001"></a>
## Overview

The `<scope>` element of the `<authorizationRules>` element specifies the virtual path of the site or application to which remote IIS Manager users and Windows users are authorized to connect when the default authorization provider, *ConfigurationAuthorizationProvider*, is enabled in Internet Information Services (IIS) 7.

> [!NOTE]
> The *ConfigurationAuthorizationProvider* uses the IIS Administration.config file to store IIS Manager authorization settings for IIS Manager; however, other authorization providers may use alternate storage locations.

<a id="002"></a>
## Compatibility

| Version | Notes |
| --- | --- |
| IIS 10.0 | The `<scope>` element was not modified in IIS 10.0. |
| IIS 8.5 | The `<scope>` element was not modified in IIS 8.5. |
| IIS 8.0 | The `<scope>` element was not modified in IIS 8.0. |
| IIS 7.5 | The `<scope>` element was not modified in IIS 7.5. |
| IIS 7.0 | The `<scope>` element of the `<authorizationRules>` element was introduced in IIS 7.0. |
| IIS 6.0 | N/A |

<a id="003"></a>
## Setup

The default installation of IIS 7 and later does not include the **Management Service** role service. To install this role service, use the following steps.

### Windows Server 2012 or Windows Server 2012 R2

1. On the taskbar, click **Server Manager**.
2. In **Server Manager**, click the **Manage** menu, and then click **Add Roles and Features**.
3. In the **Add Roles and Features** wizard, click **Next**. Select the installation type and click **Next**. Select the destination server and click **Next**.
4. On the **Server Roles** page, expand **Web Server (IIS)**, expand **Management Tools**, and then select **Management Service**. Click **Next**.  
    [![Screenshot that shows Management Service selected for Windows Server 2012.](index/_static/image2.png)](index/_static/image1.png) .
5. On the **Select features** page, click **Next**.
6. On the **Confirm installation selections** page, click **Install**.
7. On the **Results** page, click **Close**.

### Windows 8 or Windows 8.1

1. On the **Start** screen, move the pointer all the way to the lower left corner, right-click the **Start** button, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows features on or off**.
3. Expand **Internet Information Services**, expand **Web Management Tools**, and then select **IIS Management Service**.  
    [![Screenshot that shows I I S Management Service selected for Windows 8.](index/_static/image4.png)](index/_static/image3.png)
4. Click **OK**.
5. Click **Close**.

### Windows Server 2008 or Windows Server 2008 R2

1. On the taskbar, click **Start**, point to **Administrative Tools**, and then click **Server Manager**.
2. In the **Server Manager** hierarchy pane, expand **Roles**, and then click **Web Server (IIS)**.
3. In the **Web Server (IIS)** pane, scroll to the **Role Services** section, and then click **Add Role Services**.
4. On the **Select Role Services** page of the **Add Role Services Wizard**, select **Management Service**, and then click **Next**.  
    [![Screenshot that shows Management Service selected for Windows Server 2008.](index/_static/image6.png)](index/_static/image5.png)
5. On the **Confirm Installation Selections** page, click **Install**.
6. On the **Results** page, click **Close**.

### Windows Vista or Windows 7

1. On the taskbar, click **Start**, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows Features on or off**.
3. Expand **Internet Information Services**, then **Web Management Tool**.
4. Select **IIS Management Service**, and then click **OK**.   
    [![Screenshot that shows the Management Service Pane. Enable remote connections and I I S Manager credentials are selected.](index/_static/image8.png)](index/_static/image7.png)
 
<a id="004"></a>
## How To

### How to authorize an IIS Manager user for a site or application

1. Open **Internet Information Services (IIS) Manager**: 

    - If you are using Windows Server 2012 or Windows Server 2012 R2: 

        - On the taskbar, click **Server Manager**, click **Tools**, and then click **Internet Information Services (IIS) Manager**.
    - If you are using Windows 8 or Windows 8.1: 

        - Hold down the **Windows** key, press the letter **X**, and then click **Control Panel**.
        - Click **Administrative Tools**, and then double-click **Internet Information Services (IIS) Manager**.
    - If you are using Windows Server 2008 or Windows Server 2008 R2: 

        - On the taskbar, click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.
    - If you are using Windows Vista or Windows 7: 

        - On the taskbar, click **Start**, and then click **Control Panel**.
        - Double-click **Administrative Tools**, and then double-click **Internet Information Services (IIS) Manager**.
2. In the **Connections** pane, go to the connection, site, application, or directory for which you want to authorize an IIS Manager user.
3. In the **Home** pane, double-click **IIS Manager Permissions**.  
    [![Screenshot that shows the Default Web Site Home pane, with I I S Manager Permissions highlighted.](index/_static/image10.png)](index/_static/image9.png)
4. On the **IIS Manager Permissions** page, click **Allow User...** in the **Actions** pane.  
    [![Screenshot that shows the I I S Manager Permissions pane.](index/_static/image12.png)](index/_static/image11.png)
5. In the **Allow User** dialog box, choose **IIS Manager**, then click **Select...**  
    [![Screenshot that shows the Allow User dialog box, with I I S Manager selected.](index/_static/image14.png)](index/_static/image13.png)
6. In the **Users** dialog box, highlight the user account that you want to allow, and then click **OK**.  
    [![Screenshot that shows the Users dialog box, with Contoso User listed.](index/_static/image16.png)](index/_static/image15.png)
7. In the **Allow User** dialog box, click **OK**.  
    [![Screenshot that shows the Allow User dialog box, with I I S Manager selected and Contoso User added to the field.](index/_static/image18.png)](index/_static/image17.png)

<a id="005"></a>
## Configuration

### Attributes

| Attribute | Description |
| --- | --- |
| `path` | Required string attribute.<br><br>Specifies the virtual path of a site or an application. IIS Manager users and Windows users can then be added to the child [&lt;add&gt;](add.md) collection so they are authorized to connect to that site or application by using IIS Manager. |

### Child Elements

| Element | Description |
| --- | --- |
| [`add`](add.md) | Optional element.<br><br>Adds an IIS Manager user or Windows user or group to the collection of users who are authorized to connect to a site or an application by using IIS Manager. |

### Configuration Sample

The following configuration sample shows how to authorize an IIS Manager user named Contoso, a Windows group named Test Group, and a Windows user named Contoso2 to connect to the Default Web Site by using IIS Manager.

[!code-xml[Main](index/samples/sample1.xml)]

<a id="006"></a>
## Sample Code

The following code samples check to see if a `<scope>` element has already been added to the `<authorizationRules>` element for the Default Web Site; if not, a `<scope>` element is added the `<authorizationRules>` element. Next, an `<add>` element is added to the `<scope>` element that authorizes a user account named ContosoUser.

### AppCmd.exe

> [!NOTE]
> You cannot configure `<system.webServer/management/authorization>` settings using AppCmd.exe.

### C\#

[!code-csharp[Main](index/samples/sample2.cs)]

### VB.NET

[!code-vb[Main](index/samples/sample3.vb)]

### JavaScript

[!code-javascript[Main](index/samples/sample4.js)]

### VBScript

[!code-vb[Main](index/samples/sample5.vb)]
