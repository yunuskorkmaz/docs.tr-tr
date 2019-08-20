---
title: "Nasıl yapılır: WPF Uygulamalarını Dağıtmak için IIS 5.0 ve IIS 6.0'ı Yapılandırma"
ms.date: 03/30/2017
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
ms.openlocfilehash: 3a9bf79a9d505fef53b62cb589920adcf95ae92a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611496"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="86bff-102">Nasıl yapılır: WPF Uygulamalarını Dağıtmak için IIS 5.0 ve IIS 6.0'ı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="86bff-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>

<span data-ttu-id="86bff-103">Bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamayı, uygun çok amaçlı Internet posta uzantıları (MIME) türleriyle yapılandırıldığı sürece çoğu Web sunucusundan dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86bff-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate Multipurpose Internet Mail Extensions (MIME) types.</span></span> <span data-ttu-id="86bff-104">Varsayılan olarak, Microsoft Internet Information Services (IIS) 7,0 bu MIME türleriyle yapılandırılır, ancak Microsoft Internet Information Services (IIS) 5,0 ve Microsoft Internet Information Services (IIS) 6,0 değildir.</span><span class="sxs-lookup"><span data-stu-id="86bff-104">By default, Microsoft Internet Information Services (IIS) 7.0 is configured with these MIME types, but Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 are not.</span></span>

<span data-ttu-id="86bff-105">Bu konuda, uygulamaları dağıtmak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için Microsoft Internet Information Services (IIS) 5,0 ve Microsoft Internet Information Services (IIS) 6,0 ' nin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86bff-105">This topic describes how to configure Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>

> [!NOTE]
> <span data-ttu-id="86bff-106">Bir sistemin .NET Framework yüklü olup olmadığını anlamak için kayıt defterindeki *UserAgent* dizesini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86bff-106">You can check the *UserAgent* string in the registry to determine whether a system has .NET Framework installed.</span></span> <span data-ttu-id="86bff-107">.NET Framework bir sistemde yüklü olup olmadığını belirlemek üzere *UserAgent* dizesini inceleyen Ayrıntılar ve bir betik için, bkz. [.NET Framework 3,0 'Nin yüklü olup olmadığını algılama](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="86bff-107">For details and a script that examines the *UserAgent* string to determine whether .NET Framework is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="86bff-108">Içerik süre sonu ayarını ayarla</span><span class="sxs-lookup"><span data-stu-id="86bff-108">Adjust the Content Expiration Setting</span></span>

<span data-ttu-id="86bff-109">İçerik süre sonu ayarını 1 dakika olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="86bff-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="86bff-110">Aşağıdaki yordamda bunun IIS ile nasıl yapılacağı özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="86bff-110">The following procedure outlines how to do this with IIS.</span></span>

1. <span data-ttu-id="86bff-111">**Başlat** menüsüne tıklayın, **Yönetim Araçları**' nın üzerine gelın ve **Internet Information Services (IIS) Yöneticisi**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="86bff-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="86bff-112">Bu uygulamayı komut satırından "%SystemRoot%\system32\inetsrv\iis.msc" ile de başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86bff-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>

2. <span data-ttu-id="86bff-113">**Varsayılan Web sitesi** düğümünü bulana kadar IIS ağacını genişletin.</span><span class="sxs-lookup"><span data-stu-id="86bff-113">Expand the IIS tree until you find the **Default Web site** node.</span></span>

3. <span data-ttu-id="86bff-114">**Varsayılan Web sitesi** ' ne sağ tıklayın ve bağlam menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="86bff-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>

4. <span data-ttu-id="86bff-115">**Http üstbilgileri** sekmesini seçin ve "Içerik süre sonunu etkinleştir" e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="86bff-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>

5. <span data-ttu-id="86bff-116">İçeriği 1 dakika sonra dolacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="86bff-116">Set the content to expire after 1 minute.</span></span>

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="86bff-117">MIME türlerini ve dosya uzantılarını Kaydet</span><span class="sxs-lookup"><span data-stu-id="86bff-117">Register MIME Types and File Extensions</span></span>

<span data-ttu-id="86bff-118">İstemci sistemindeki tarayıcının doğru işleyiciyi yükleyebilmesi için birkaç MIME türünü ve dosya uzantısını kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="86bff-118">You must register several MIME types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="86bff-119">Aşağıdaki türleri eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="86bff-119">You need to add the following types:</span></span>

|<span data-ttu-id="86bff-120">Dahili numara</span><span class="sxs-lookup"><span data-stu-id="86bff-120">Extension</span></span>|<span data-ttu-id="86bff-121">MIME türü</span><span class="sxs-lookup"><span data-stu-id="86bff-121">MIME Type</span></span>|
|---------------|---------------|
|<span data-ttu-id="86bff-122">. manifest</span><span class="sxs-lookup"><span data-stu-id="86bff-122">.manifest</span></span>|<span data-ttu-id="86bff-123">uygulama/bildirim</span><span class="sxs-lookup"><span data-stu-id="86bff-123">application/manifest</span></span>|
|<span data-ttu-id="86bff-124">. xaml</span><span class="sxs-lookup"><span data-stu-id="86bff-124">.xaml</span></span>|<span data-ttu-id="86bff-125">uygulama/xaml + xml</span><span class="sxs-lookup"><span data-stu-id="86bff-125">application/xaml+xml</span></span>|
|<span data-ttu-id="86bff-126">. Application</span><span class="sxs-lookup"><span data-stu-id="86bff-126">.application</span></span>|<span data-ttu-id="86bff-127">uygulama/x-MS-uygulama</span><span class="sxs-lookup"><span data-stu-id="86bff-127">application/x-ms-application</span></span>|
|<span data-ttu-id="86bff-128">. xbap</span><span class="sxs-lookup"><span data-stu-id="86bff-128">.xbap</span></span>|<span data-ttu-id="86bff-129">uygulama/x-MS-XBAP</span><span class="sxs-lookup"><span data-stu-id="86bff-129">application/x-ms-xbap</span></span>|
|<span data-ttu-id="86bff-130">. deploy</span><span class="sxs-lookup"><span data-stu-id="86bff-130">.deploy</span></span>|<span data-ttu-id="86bff-131">Uygulama/sekizli-akış</span><span class="sxs-lookup"><span data-stu-id="86bff-131">application/octet-stream</span></span>|
|<span data-ttu-id="86bff-132">. XPS</span><span class="sxs-lookup"><span data-stu-id="86bff-132">.xps</span></span>|<span data-ttu-id="86bff-133">application/vnd. MS-XpsDocument</span><span class="sxs-lookup"><span data-stu-id="86bff-133">application/vnd.ms-xpsdocument</span></span>|

> [!NOTE]
> <span data-ttu-id="86bff-134">İstemci sistemlerine MIME türlerini veya dosya uzantılarını kaydetmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="86bff-134">You do not need to register MIME types or file extensions on client systems.</span></span> <span data-ttu-id="86bff-135">Microsoft .NET Framework 'Ü yüklediğinizde otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="86bff-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>

<span data-ttu-id="86bff-136">Aşağıdaki Microsoft Visual Basic Scripting Edition (VBScript) örneği, gerekli MIME türlerini otomatik olarak IIS 'e ekler.</span><span class="sxs-lookup"><span data-stu-id="86bff-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary MIME types to IIS.</span></span> <span data-ttu-id="86bff-137">Betiği kullanmak için, kodu sunucunuzdaki bir. vbs dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="86bff-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="86bff-138">Ardından, komut satırından dosyasını çalıştırarak veya içindeki [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)]dosyasına çift tıklayarak betiği çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="86bff-138">Then, run the script by running the file from the command line or double-clicking the file in [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span></span>

```vb
' This script adds the necessary Windows Presentation Foundation MIME types
' to an IIS Server.
' To use this script, just double-click or execute it from a command line.
' Running this script multiple times results in multiple entries in the IIS MimeMap.

Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec
Const ADS_PROPERTY_UPDATE = 2

' Set the MIME types to be added
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _
    "application/xaml+xml", ".application", "application/x-ms-application", _
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _
    ".xps", "application/vnd.ms-xpsdocument")

' Get the MimeMap object
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")

' Call AddMimeType for every pair of extension/MIME type
For counter = 0 to UBound(MimeTypesToAddArray) Step 2
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)
Next

' Create a Shell object
Set WshShell = CreateObject("WScript.Shell")

' Stop and Start the IIS Service
Set oExec = WshShell.Exec("net stop w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = WshShell.Exec("net start w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = Nothing

' Report status to user
WScript.Echo "Windows Presentation Foundation MIME types have been registered."

' AddMimeType Sub
Sub AddMimeType (Ext, MType)

    ' Get the mappings from the MimeMap property.
    MimeMapArray = MimeMapObj.GetEx("MimeMap")

    ' Add a new mapping.
    i = UBound(MimeMapArray) + 1
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> <span data-ttu-id="86bff-139">Bu betiği birden çok kez çalıştırmak, Microsoft Internet Information Services (IIS) 5,0 veya Microsoft Internet Information Services (IIS) 6,0 metatabanında birden çok MIME eşleme girişi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86bff-139">Running this script multiple times creates multiple MIME map entries in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

<span data-ttu-id="86bff-140">Bu betiği çalıştırdıktan sonra, Microsoft Internet Information Services (IIS) 5,0 veya Microsoft Internet Information Services (IIS) 6,0 Microsoft Yönetim Konsolu 'ndan (MMC) ek MIME türleri göremeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86bff-140">After you have run this script, you may not see additional MIME types from the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 Microsoft Management Console (MMC).</span></span> <span data-ttu-id="86bff-141">Ancak, bu MIME türleri Microsoft Internet Information Services (IIS) 5,0 veya Microsoft Internet Information Services (IIS) 6,0 metabase 'e eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="86bff-141">However, these MIME types have been added to the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span> <span data-ttu-id="86bff-142">Aşağıdaki betik, Microsoft Internet Information Services (IIS) 5,0 veya Microsoft Internet Information Services (IIS) 6,0 metatabanındaki tüm MIME türlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="86bff-142">The following script will display all the MIME types in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

<span data-ttu-id="86bff-143">Betiği bir `.vbs` dosya olarak kaydedin (örneğin, `DiscoverIISMimeTypes.vbs`) ve aşağıdaki komutu kullanarak komut isteminden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="86bff-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>

```console
cscript DiscoverIISMimeTypes.vbs
```
