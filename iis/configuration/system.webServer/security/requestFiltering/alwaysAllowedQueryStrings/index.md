---
title: "Always Allowed Query Strings &lt;alwaysAllowedQueryStrings&gt;"
author: rick-anderson
description: "Overview The &lt;alwaysAllowedQueryStrings&gt; element specifies a collection of query strings that request filtering will always allow. The &lt;alwaysAllowe..."
ms.date: 09/26/2016
ms.assetid: 6edd56a4-101f-4dc9-b24a-99625ac1ed49
msc.legacyurl: /configreference/system.webserver/security/requestfiltering/alwaysallowedquerystrings
msc.type: config
ms.custom: sfi-image-nochange
---
# Always Allowed Query Strings &lt;alwaysAllowedQueryStrings&gt;

<a id="001"></a>
## Overview

The `<alwaysAllowedQueryStrings>` element specifies a collection of query strings that request filtering will always allow. The `<alwaysAllowedQueryStrings>` element contains a collection of [`<add>`](add.md) elements that specify query string patterns that request filtering will allow, which override the values in the [`<denyQueryStringSequences>`](../denyquerystringsequences/index.md) collection.

<a id="002"></a>
## Compatibility

| Version | Notes |
| --- | --- |
| IIS 10.0 | The `<alwaysAllowedQueryStrings>` element was not modified in IIS 10.0. |
| IIS 8.5 | The `<alwaysAllowedQueryStrings>` element was not modified in IIS 8.5. |
| IIS 8.0 | The `<alwaysAllowedQueryStrings>` element was not modified in IIS 8.0. |
| IIS 7.5 | The `<alwaysAllowedQueryStrings>` element of the `<requestFiltering>` element ships as a feature of IIS 7.5. |
| IIS 7.0 | The `<alwaysAllowedQueryStrings>` element of the `<requestFiltering>` element was introduced as an update for IIS 7.0 that is available through Microsoft Knowledge Base Article 957508 (`https://support.microsoft.com/kb/957508`). |
| IIS 6.0 | The `<alwaysAllowedQueryStrings>` element is roughly analogous to the **[AlwaysAllowedQueryStrings]** section that was added to URLScan 3.0. |

<a id="003"></a>
## Setup

The default installation of IIS 7 and later includes the Request Filtering role service or feature. If the Request Filtering role service or feature is uninstalled, you can reinstall it using the following steps.

### Windows Server 2012 or Windows Server 2012 R2

1. On the taskbar, click **Server Manager**.
2. In **Server Manager**, click the **Manage** menu, and then click **Add Roles and Features**.
3. In the **Add Roles and Features** wizard, click **Next**. Select the installation type and click **Next**. Select the destination server and click **Next**.
4. On the **Server Roles** page, expand **Web Server (IIS)**, expand **Web Server**, expand **Security**, and then select **Request Filtering**. Click **Next**.  
    [![Image of Security pane in Server Roles page expanded displaying Request Filtering highlighted.](index/_static/image2.png)](index/_static/image1.png) .
5. On the **Select features** page, click **Next**.
6. On the **Confirm installation selections** page, click **Install**.
7. On the **Results** page, click **Close**.

### Windows 8 or Windows 8.1

1. On the **Start** screen, move the pointer all the way to the lower left corner, right-click the **Start** button, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows features on or off**.
3. Expand **Internet Information Services**, expand **World Wide Web Services**, expand **Security**, and then select **Request Filtering**.  
    [![Image of Security and World Wide Web Services pane expanded and Request Filtering option selected.](index/_static/image4.png)](index/_static/image3.png)
4. Click **OK**.
5. Click **Close**.

### Windows Server 2008 or Windows Server 2008 R2

1. On the taskbar, click **Start**, point to **Administrative Tools**, and then click **Server Manager**.
2. In the **Server Manager** hierarchy pane, expand **Roles**, and then click **Web Server (IIS)**.
3. In the **Web Server (IIS)** pane, scroll to the **Role Services** section, and then click **Add Role Services**.
4. On the **Select Role Services** page of the **Add Role Services Wizard**, select **Request Filtering**, and then click **Next**.   
    [![Screenshot of World Wide Web Services and Security pane expanded with Request Filtering selected.](index/_static/image6.png)](index/_static/image5.png)
5. On the **Confirm Installation Selections** page, click **Install**.
6. On the **Results** page, click **Close**.

### Windows Vista or Windows 7

1. On the taskbar, click **Start**, and then click **Control Panel**.
2. In **Control Panel**, click **Programs and Features**, and then click **Turn Windows Features on or off**.
3. Expand **Internet Information Services**, then **World Wide Web Services**, and then **Security**.
4. Select **Request Filtering**, and then click **OK**.   
    [![Image of Internet Information Services and World Wide Web pane displaying Request Filtering selected.](index/_static/image8.png)](index/_static/image7.png)
 
<a id="004"></a>
## How To

### How to allow a query string sequence

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
2. In the Connections pane, go to the connection, site, application, or directory for which you want to modify your request filtering settings.
3. In the **Home** pane, double-click **Request Filtering**.
4. In the **Request Filtering** pane, click the **Query Strings** tab, and then click **Allow Query String...** in the **Actions** pane.
5. In the **Allow Query String** dialog box, enter the query string sequence that you wish to block, and then click **OK**.

<a id="005"></a>
## Configuration

The `<alwaysAllowedQueryStrings>` element of the `<requestFiltering>` element is configured at the site, application, or directory level.

### Attributes

None.

### Child Elements

| Element | Description |
| --- | --- |
| [`add`](add.md) | Optional element. Adds a query string pattern to the collection of query strings that request filtering will always allow. |
| `clear` | Optional element.<br><br>Clears the collection of query string patterns that request filtering will always allow. |
| `remove` | Optional element.<br><br>Removes a query string pattern from the collection of query strings that request filtering will always allow. |

### Configuration Sample

The following sample illustrates a combination of a `<denyQueryStringSequences>` element and an `<alwaysAllowedQueryStrings>` element that will deny any query strings if they contain either of two specific character sequences, but will always allow a specific query string that contains both of those two specific character sequences in a particular order.

[!code-xml[Main](index/samples/sample1.xml)]

<a id="006"></a>
## Sample Code

The following examples demonstrate how to add a query string that will always be allowed on the Default Web Site.

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
