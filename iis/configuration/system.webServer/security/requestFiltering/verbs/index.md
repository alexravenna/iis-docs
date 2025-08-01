---
title: "Verbs &lt;verbs&gt;"
author: rick-anderson
description: "Overview The &lt;verbs&gt; element specifies which HTTP verbs are allowed or denied to limit the type of HTTP requests that are allowed by the Web server. No..."
ms.date: 09/26/2016
ms.assetid: fd402a22-694b-4982-a82d-189ce7be938a
msc.legacyurl: /configreference/system.webserver/security/requestfiltering/verbs
msc.type: config
ms.custom: sfi-image-nochange
---
# Verbs &lt;verbs&gt;

<a id="001"></a>
## Overview

The `<verbs>` element specifies which HTTP verbs are allowed or denied to limit the type of HTTP requests that are allowed by the Web server.

> [!NOTE]
> When request filtering blocks an HTTP request because of a denied HTTP verb, IIS 7 will return an HTTP 404 error to the client and log the following HTTP status with a unique substatus that identifies the reason that the request was denied:

| HTTP Substatus | Description |
| --- | --- |
| `404.6` | Verb Denied |

This substatus allows Web administrators to analyze their IIS logs and identify potential threats.

<a id="002"></a>
## Compatibility

| Version | Notes |
| --- | --- |
| IIS 10.0 | The `<verbs>` element was not modified in IIS 10.0. |
| IIS 8.5 | The `<verbs>` element was not modified in IIS 8.5. |
| IIS 8.0 | The `<verbs>` element was not modified in IIS 8.0. |
| IIS 7.5 | The `<verbs>` element was not modified in IIS 7.5. |
| IIS 7.0 | The `<verbs>` element of the `<requestFiltering>` collection was introduced in IIS 7.0. |
| IIS 6.0 | The `<verbs>` element replaces the IIS 6.0 UrlScan **[AllowVerbs]** and **[DenyVerbs]** features. |

<a id="003"></a>
## Setup

The default installation of IIS 7 and later includes the Request Filtering role service or feature. If the Request Filtering role service or feature is uninstalled, you can reinstall it using the following steps.

### Windows Server 2012 or Windows Server 2012 R2

1. On the taskbar, click **Server Manager**.
2. In **Server Manager**, click the **Manage** menu, and then click **Add Roles and Features**.
3. In the **Add Roles and Features** wizard, click **Next**. Select the installation type and click **Next**. Select the destination server and click **Next**.
4. On the **Server Roles** page, expand **Web Server (IIS)**, expand **Web Server**, expand **Security**, and then select **Request Filtering**. Click **Next**.  
    [![Screenshot shows Web Server and Security pane expanded with Request filtering highlighted.](index/_static/image2.png)](index/_static/image1.png) .
5. On the **Select features** page, click **Next**.
6. On the **Confirm installation selections** page, click **Install**.
7. On the **Results** page, click **Close**.

### Windows 8 or Windows 8.1

1. On the **Start** screen, move the pointer all the way to the lower left corner, right-click the **Start** button, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows features on or off**.
3. Expand **Internet Information Services**, expand **World Wide Web Services**, expand **Security**, and then select **Request Filtering**.  
    [![Screenshot of World Wide web Services and Security pane expanded with Request Filtering highlighted.](index/_static/image4.png)](index/_static/image3.png)
4. Click **OK**.
5. Click **Close**.

### Windows Server 2008 or Windows Server 2008 R2

1. On the taskbar, click **Start**, point to **Administrative Tools**, and then click **Server Manager**.
2. In the **Server Manager** hierarchy pane, expand **Roles**, and then click **Web Server (IIS)**.
3. In the **Web Server (IIS)** pane, scroll to the **Role Services** section, and then click **Add Role Services**.
4. On the **Select Role Services** page of the **Add Role Services Wizard**, select **Request Filtering**, and then click **Next**.   
    [![Screenshot displays Security pane expanded in Select Role services page and Request Filtering selected.](index/_static/image6.png)](index/_static/image5.png)
5. On the **Confirm Installation Selections** page, click **Install**.
6. On the **Results** page, click **Close**.

### Windows Vista or Windows 7

1. On the taskbar, click **Start**, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows Features on or off**.
3. Expand **Internet Information Services**, then **World Wide Web Services**, and then **Security**.
4. Select **Request Filtering**, and then click **OK**.   
    [![Screenshot of Internet Information Services and World Wide Web Service node expanded. Request Filtering is selected.](index/_static/image8.png)](index/_static/image7.png)
 
<a id="004"></a>
## How To

**Note for IIS 7.0 users**: Some of the steps in this section may require that you install the Microsoft Administration Pack for IIS 7.0, which includes a user interface for request filtering. To install the Microsoft Administration Pack for IIS 7.0, please see the following URL:

- [https://www.iis.net/expand/AdministrationPack](https://www.iis.net/downloads/microsoft/administration-pack)
 
### How to deny an HTTP verb

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
2. In the **Connections** pane, go to the connection, site, application, or directory for which you want to modify your request filtering settings.
3. In the **Home** pane, double-click **Request Filtering**.   
    [![Screenshot of Default Web Site Home pane showing Request Filtering selected.](index/_static/image10.png)](index/_static/image9.png)
4. In the **Request Filtering** pane, click the **HTTP verbs** tab, and then click **Deny Verb...** in the **Actions** pane.   
    [![Screenshot shows Request Filtering pane with H T T P verbs tab and Deny Verb option in Actions pane.](index/_static/image12.png)](index/_static/image11.png)
5. In the **Deny Verb** dialog box, enter the HTTP verb that you wish to block, and then click **OK**.   
    [![Screenshot of Deny Verb dialog box showing H T T P verb box.](index/_static/image14.png)](index/_static/image13.png)

    For example, to prevent HTTP TRACE requests to your server, you would enter "TRACE" in the dialog box.
 
<a id="005"></a>
## Configuration

### Attributes

| Attribute | Description |
| --- | --- |
| `allowUnlisted` | Optional Boolean attribute. <br><br>Specifies whether the Web server should process unlisted verbs. If you set this attribute to **true**, you must list all verbs you want to deny. If you set this attribute to **false**, you must list all verbs that you want to allow. <br><br>The default value is `true`. |
| `applyToWebDAV` | Optional Boolean attribute. <br><br>Specifies whether these settings should also apply to WebDAV requests. |

### Child Elements

| Element | Description |
| --- | --- |
| [`add`](add.md) | Optional element.<br><br>Adds a verb to the verbs collection. |
| `clear` | Optional element.<br><br>Removes all references to verbs from the verbs collection. |
| `remove` | Optional element.<br><br>Removes a reference to a verb from the verbs collection. |

### Configuration Sample

The following example Web.config file will configure two options: it will configure IIS to deny HTTP PUT requests, and it will configure request filtering to allow WebDAV access to all HTTP verbs.

[!code-xml[Main](index/samples/sample1.xml)]

<a id="006"></a>
## Sample Code

The following code samples will configure two options: they will configure IIS to deny HTTP PUT requests for the &quot;Default Web Site&quot;, and they will configure request filtering to allow WebDAV access to all HTTP verbs.

### AppCmd.exe

[!code-console[Main](index/samples/sample2.cmd)]

### PowerShell

[!code-powershell[Main](index/samples/sample7.ps1)]

### C\#

[!code-csharp[Main](index/samples/sample3.cs)]

### VB.NET

[!code-vb[Main](index/samples/sample4.vb)]

### JavaScript

[!code-javascript[Main](index/samples/sample5.js)]

### VBScript

[!code-vb[Main](index/samples/sample6.vb)]
