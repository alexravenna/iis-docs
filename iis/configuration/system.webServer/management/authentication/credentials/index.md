---
title: "Management Authentication Credentials &lt;credentials&gt;"
author: rick-anderson
description: "Overview The &lt;credentials&gt; element of the &lt;authentication&gt; element specifies credentials for IIS Manager user accounts. IIS Manager users can use..."
ms.date: 09/26/2016
ms.assetid: 89e76258-0814-4d50-8da1-60db5f92f1c2
msc.legacyurl: /configreference/system.webserver/management/authentication/credentials
msc.type: config
ms.custom: sfi-image-nochange
---
# Management Authentication Credentials &lt;credentials&gt;

<a id="001"></a>
## Overview

The `<credentials>` element of the `<authentication>` element specifies credentials for IIS Manager user accounts. IIS Manager users can use IIS Manager to connect to sites and applications for which they are authorized by a server administrator.

> [!NOTE]
> The `<credentials>` element only applies when you use the default *ConfigurationAuthenticationProvider* as your authentication provider.

<a id="002"></a>
## Compatibility

| Version | Notes |
| --- | --- |
| IIS 10.0 | The `<credentials>` element was not modified in IIS 10.0. |
| IIS 8.5 | The `<credentials>` element was not modified in IIS 8.5. |
| IIS 8.0 | The `<credentials>` element was not modified in IIS 8.0. |
| IIS 7.5 | The `<credentials>` element was not modified in IIS 7.5. |
| IIS 7.0 | The `<credentials>` element of the `<authentication>` element was introduced in IIS 7.0. |
| IIS 6.0 | N/A |

<a id="003"></a>
## Setup

The default installation of IIS 7 and later does not include the **Management Service** role service. To install this role service, use the following steps.

### Windows Server 2012 or Windows Server 2012 R2

1. On the taskbar, click **Server Manager**.
2. In **Server Manager**, click the **Manage** menu, and then click **Add Roles and Features**.
3. In the **Add Roles and Features** wizard, click **Next**. Select the installation type and click **Next**. Select the destination server and click **Next**.
4. On the **Server Roles** page, expand **Web Server (IIS)**, expand **Management Tools**, and then select **Management Service**. Click **Next**.  
    [![Image of Web Server I I S and Management Tools pane expanded with Management Service selected.](index/_static/image2.png)](index/_static/image1.png) .
5. On the **Select features** page, click **Next**.
6. On the **Confirm installation selections** page, click **Install**.
7. On the **Results** page, click **Close**.

### Windows 8 or Windows 8.1

1. On the **Start** screen, move the pointer all the way to the lower left corner, right-click the **Start** button, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows features on or off**.
3. Expand **Internet Information Services**, expand **Web Management Tools**, and then select **IIS Management Service**.  
    [![Screenshot of Internet Information Services and Web Management Tools pane expanded with I I S Management Service selected.](index/_static/image4.png)](index/_static/image3.png)
4. Click **OK**.
5. Click **Close**.

### Windows Server 2008 or Windows Server 2008 R2

1. On the taskbar, click **Start**, point to **Administrative Tools**, and then click **Server Manager**.
2. In the **Server Manager** hierarchy pane, expand **Roles**, and then click **Web Server (IIS)**.
3. In the **Web Server (IIS)** pane, scroll to the **Role Services** section, and then click **Add Role Services**.
4. On the **Select Role Services** page of the **Add Role Services Wizard**, select **Management Service**, and then click **Next**.  
    [![Image of Select Role Services page with Management Tools pane expanded and Management Service selected.](index/_static/image6.png)](index/_static/image5.png)
5. On the **Confirm Installation Selections** page, click **Install**.
6. On the **Results** page, click **Close**.

### Windows Vista or Windows 7

1. On the taskbar, click **Start**, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows Features on or off**.
3. Expand **Internet Information Services**, then **Web Management Tool**.
4. Select **IIS Management Service**, and then click **OK**.   
    [![Image of Management Service feature dialog box with Enable remote connections selected.](index/_static/image8.png)](index/_static/image7.png)
 
<a id="004"></a>
## How To

### How to enable IIS Manager credentials for a server

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
2. In the **Connections** pane, click the server name.
3. In the server's **Home** pane, double-click **Management Service**.  
    [![Screenshot of Servers Home pane displaying Management Service highlighted.](index/_static/image10.png)](index/_static/image9.png)
4. On the **Management Service** page, choose **Windows credentials or IIS Manager credentials**, then click **Apply** in the **Actions** pane.  
    [![Screenshot of Management Service page with Windows Credentials or I I S Manager Credentials selected.](index/_static/image12.png)](index/_static/image11.png)

### How to add IIS Manager user credentials to a server

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
2. In the **Connections** pane, click the server name.
3. In the server's **Home** pane, double-click **IIS Manager Users**.  
    [![Screenshot of servers Home pane displaying I I S Manager Users highlighted.](index/_static/image14.png)](index/_static/image13.png)
4. On the **IIS Manager Users** page, click **Add User...** in the **Actions** pane.  
    [![Screenshot of I I S Manager Users page.](index/_static/image16.png)](index/_static/image15.png)
5. In the **Add User** dialog box, enter the user name and password, and then click **OK**.  
    [![Image of Add User dialog box showing User name and Password typed in the respective fields.](index/_static/image18.png)](index/_static/image17.png)

<a id="005"></a>
## Configuration

### Attributes

None.

### Child Elements

| Element | Description |
| --- | --- |
| [`add`](add.md) | Optional element. <br><br>Adds an IIS Manager user account to the collection of IIS Manager users. |

### Configuration Sample

The following configuration sample shows how to add an IIS Manager user named ContosoUser to Administration.config.

[!code-xml[Main](index/samples/sample1.xml)]

<a id="006"></a>
## Sample Code

The following code samples add an IIS Manager user account named ContosoUser to IIS 7.

### AppCmd.exe

> [!NOTE]
> You cannot configure `<system.webServer/management/authentication>` settings using AppCmd.exe.

### C\#

[!code-csharp[Main](index/samples/sample2.cs)]

### VB.NET

[!code-vb[Main](index/samples/sample3.vb)]

### JavaScript

[!code-javascript[Main](index/samples/sample4.js)]

### VBScript

[!code-vb[Main](index/samples/sample5.vb)]
