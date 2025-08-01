---
title: "Adding Management Authorization Providers &lt;add&gt;"
author: rick-anderson
description: "Overview The &lt;add&gt; element of the &lt;providers&gt; element adds an authorization provider to the collection of management authorization providers for..."
ms.date: 09/26/2016
ms.assetid: 2ffa0a51-95f0-4e94-bbe2-8706ddfcf4f9
msc.legacyurl: /configreference/system.webserver/management/authorization/providers/add
msc.type: config
ms.custom: sfi-image-nochange
---
# Adding Management Authorization Providers &lt;add&gt;

<a id="001"></a>
## Overview

The `<add>` element of the `<providers>` element adds an authorization provider to the collection of management authorization providers for Internet Information Services (IIS) 7.

> [!NOTE]
> The default authorization provider, *ConfigurationAuthorizationProvider*, uses the IIS Administration.config file to store authorization rules for IIS Manager.

<a id="002"></a>
## Compatibility

| Version | Notes |
| --- | --- |
| IIS 10.0 | The `<add>` element was not modified in IIS 10.0. |
| IIS 8.5 | The `<add>` element was not modified in IIS 8.5. |
| IIS 8.0 | The `<add>` element was not modified in IIS 8.0. |
| IIS 7.5 | The `<add>` element was not modified in IIS 7.5. |
| IIS 7.0 | The `<add>` element of the `<providers>` element was introduced in IIS 7.0. |
| IIS 6.0 | N/A |

<a id="003"></a>
## Setup

The default installation of IIS 7 and later does not include the **Management Service** role service. To install this role service, use the following steps.

### Windows Server 2012 or Windows Server 2012 R2

1. On the taskbar, click **Server Manager**.
2. In **Server Manager**, click the **Manage** menu, and then click **Add Roles and Features**.
3. In the **Add Roles and Features** wizard, click **Next**. Select the installation type and click **Next**. Select the destination server and click **Next**.
4. On the **Server Roles** page, expand **Web Server (IIS)**, expand **Management Tools**, and then select **Management Service**. Click **Next**.  
    [![Screenshot of the Server Roles page. Management Tools is expanded. Management Service is selected and highlighted.](add/_static/image2.png)](add/_static/image1.png) .

5. On the **Select features** page, click **Next**.
6. On the **Confirm installation selections** page, click **Install**.
7. On the **Results** page, click **Close**.

### Windows 8 or Windows 8.1

1. On the **Start** screen, move the pointer all the way to the lower left corner, right-click the **Start** button, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows features on or off**.
3. Expand **Internet Information Services**, expand **Web Management Tools**, and then select **IIS Management Service**.  
    [![Screenshot of the navigation tree in Programs and Features. The I I S Management Service folder is highlighted and selected.](add/_static/image4.png)](add/_static/image3.png)
4. Click **OK**.
5. Click **Close**.

### Windows Server 2008 or Windows Server 2008 R2

1. On the taskbar, click **Start**, point to **Administrative Tools**, and then click **Server Manager**.
2. In the **Server Manager** hierarchy pane, expand **Roles**, and then click **Web Server (IIS)**.
3. In the **Web Server (IIS)** pane, scroll to the **Role Services** section, and then click **Add Role Services**.
4. On the **Select Role Services** page of the **Add Role Services Wizard**, select **Management Service**, and then click **Next**.  
    [![Screenshot of the Select Role Services page. This page is found in the Add Role Services Wizard. Management Service is selected and highlighted.](add/_static/image6.png)](add/_static/image5.png)
5. On the **Confirm Installation Selections** page, click **Install**.
6. On the **Results** page, click **Close**.

### Windows Vista or Windows 7

1. On the taskbar, click **Start**, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows Features on or off**.
3. Expand **Internet Information Services**, then **Web Management Tool**.
4. Select **IIS Management Service**, and then click **OK**.   
    [![Screenshot of the I I S Management Service page. Enable remote connections is selected.](add/_static/image8.png)](add/_static/image7.png)
 
<a id="004"></a>
## How To

There is no user interface for configuring the `<providers>` element of the `<authorization>` element for IIS 7. For examples of how to configure the `<providers>` element of the `<authorization>` element programmatically, see the [Code Samples](#006) section of this document.

<a id="005"></a>
## Configuration

### Attributes

| Attribute | Description |
| --- | --- |
| `name` | Required string attribute.<br><br>Specifies the name of the authorization provider. |
| `type` | Required string attribute.<br><br>Specifies the authentication provider's managed type. |

### Child Elements

None.

### Configuration Sample

The following default `<providers>` element under the `<authorization>` element is configured in the root Administration.config file in IIS 7 when the Management Service role service is installed.

[!code-xml[Main](add/samples/sample1.xml)]

<a id="006"></a>
## Sample Code

> [!NOTE]
> The examples in this document illustrate using a managed-code assembly that has been stored in the .NET Global Assembly Cache (GAC). Before using the code in these examples to deploy your own assemblies, you need to retrieve the assembly information from the GAC. To do so, use the following steps:

- In Windows Explorer, open your C:\Windows\assembly path, where C: is your operating system drive.
- Locate your assembly.
- Right-click the assembly and click **Properties**.
- Copy the **Culture** value; for example: **Neutral**.
- Copy the **Version** number; for example: **1.0.0.0**.
- Copy the **Public Key Token** value; for example: **426f62526f636b73**.
- Click **Cancel**.

The following code examples add an authorization provider named ContosoAuthorizationProvider to the collection of management authorization providers, and set the default authorization provider to ContosoAuthorizationProvider.

### AppCmd.exe

> [!NOTE]
> You cannot configure `<system.webServer/Management>` settings using AppCmd.exe.

### C\#

[!code-csharp[Main](add/samples/sample2.cs)]

### VB.NET

[!code-vb[Main](add/samples/sample3.vb)]

### JavaScript

[!code-javascript[Main](add/samples/sample4.js)]

### VBScript

[!code-vb[Main](add/samples/sample5.vb)]
