---
title: "Management Authorization Rules &lt;authorizationRules&gt;"
author: rick-anderson
description: "Overview The &lt;authorizationRules&gt; element of the &lt;authorization&gt; element specifies which IIS Manager users and Windows users are authorized to co..."
ms.date: 09/26/2016
ms.assetid: 729a264b-3faa-4803-976d-413b89769cc0
msc.legacyurl: /configreference/system.webserver/management/authorization/authorizationrules
msc.type: config
ms.custom: sfi-image-nochange
---
# Management Authorization Rules &lt;authorizationRules&gt;

<a id="001"></a>
## Overview

The `<authorizationRules>` element of the `<authorization>` element specifies which IIS Manager users and Windows users are authorized to connect to a site or an application by using IIS Manager when the default authorization provider, *ConfigurationAuthorizationProvider*, is enabled in Internet Information Services (IIS) 7.

> [!NOTE]
> The *ConfigurationAuthorizationProvider* uses the IIS Administration.config file to store IIS Manager authorization settings for IIS Manager; however, other authorization providers may use alternate storage locations.

<a id="002"></a>
## Compatibility

| Version | Notes |
| --- | --- |
| IIS 10.0 | The `<authorizationRules>` element was not modified in IIS 10.0. |
| IIS 8.5 | The `<authorizationRules>` element was not modified in IIS 8.5. |
| IIS 8.0 | The `<authorizationRules>` element was not modified in IIS 8.0. |
| IIS 7.5 | The `<authorizationRules>` element was not modified in IIS 7.5. |
| IIS 7.0 | The `<authorizationRules>` element of the `<authorization>` element was introduced in IIS 7.0. |
| IIS 6.0 | N/A |

<a id="003"></a>
## Setup

The default installation of IIS 7 and later does not include the **Management Service** role service. To install this role service, use the following steps.

### Windows Server 2012 or Windows Server 2012 R2

1. On the taskbar, click **Server Manager**.
2. In **Server Manager**, click the **Manage** menu, and then click **Add Roles and Features**.
3. In the **Add Roles and Features** wizard, click **Next**. Select the installation type and click **Next**. Select the destination server and click **Next**.
4. On the **Server Roles** page, expand **Web Server (IIS)**, expand **Management Tools**, and then select **Management Service**. Click **Next**.  
    [![Screenshot on the Server Roles page with the Management Service option being highlighted.](index/_static/image2.png)](index/_static/image1.png) .
5. On the **Select features** page, click **Next**.
6. On the **Confirm installation selections** page, click **Install**.
7. On the **Results** page, click **Close**.

### Windows 8 or Windows 8.1

1. On the **Start** screen, move the pointer all the way to the lower left corner, right-click the **Start** button, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows features on or off**.
3. Expand **Internet Information Services**, expand **Web Management Tools**, and then select **IIS Management Service**.  
    [![Screenshot of the Internet Information Services folder with the I I S Management Service folder being highlighted.](index/_static/image4.png)](index/_static/image3.png)
4. Click **OK**.
5. Click **Close**.

### Windows Server 2008 or Windows Server 2008 R2

1. On the taskbar, click **Start**, point to **Administrative Tools**, and then click **Server Manager**.
2. In the **Server Manager** hierarchy pane, expand **Roles**, and then click **Web Server (IIS)**.
3. In the **Web Server (IIS)** pane, scroll to the **Role Services** section, and then click **Add Role Services**.
4. On the **Select Role Services** page of the **Add Role Services Wizard**, select **Management Service**, and then click **Next**.  
    [![Screenshot of the Add Role Services Wizard with the Management Service option being highlighted.](index/_static/image6.png)](index/_static/image5.png)
5. On the **Confirm Installation Selections** page, click **Install**.
6. On the **Results** page, click **Close**.

### Windows Vista or Windows 7

1. On the taskbar, click **Start**, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows Features on or off**.
3. Expand **Internet Information Services**, then **Web Management Tool**.
4. Select **IIS Management Service**, and then click **OK**.   
    [![Screenshot of the Management Service screen with the Enable remote connections option being selected.](index/_static/image8.png)](index/_static/image7.png)
 
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
    [![Screenshot of the I I S Manager Permissions shortcut in the Home pane.](index/_static/image10.png)](index/_static/image9.png)
4. On the **IIS Manager Permissions** page, click **Allow User...** in the **Actions** pane.  
    [![Screenshot of the I I S Manager Permissions page.](index/_static/image12.png)](index/_static/image11.png)
5. In the **Allow User** dialog box, choose **IIS Manager**, then click **Select...**  
    [![Screenshot of the Allow User dialog box with I I S Manager option being selected.](index/_static/image14.png)](index/_static/image13.png)
6. In the **Users** dialog box, highlight the user account that you want to allow, and then click **OK**.  
    [![Screenshot of the Users dialog box with the user account being highlighted.](index/_static/image16.png)](index/_static/image15.png)
7. In the **Allow User** dialog box, click **OK**.  
    [![Screenshot of the Allow User dialog box with the selected user account populating the I I S Manager field.](index/_static/image18.png)](index/_static/image17.png)

<a id="005"></a>
## Configuration

### Attributes

None.

### Child Elements

| Element | Description |
| --- | --- |
| [`scope`](scope/index.md) | Optional element. <br><br>Configures the virtual path of the site or application to which IIS Manager users and Windows users are authorized to connect by using IIS Manager. |

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
