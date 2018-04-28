---
title: "Nasıl yapılır: WPF Uygulamalarını Dağıtmak için IIS 5.0 ve IIS 6.0'ı Yapılandırma"
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c1b03cf39608566ed80e2288204480e77994ad7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="91a98-102">Nasıl yapılır: WPF Uygulamalarını Dağıtmak için IIS 5.0 ve IIS 6.0'ı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="91a98-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>
<span data-ttu-id="91a98-103">Dağıtabilmeniz için bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çoğu Web sunucularından uygulama uygun ile yapılandırılmış olan sürece [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] türleri.</span><span class="sxs-lookup"><span data-stu-id="91a98-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] types.</span></span> <span data-ttu-id="91a98-104">Varsayılan olarak, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] ile yapılandırılmıştır [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türleri, ancak [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ve [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] değil.</span><span class="sxs-lookup"><span data-stu-id="91a98-104">By default, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] is configured with these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types, but [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] are not.</span></span>  
  
 <span data-ttu-id="91a98-105">Bu konuda nasıl yapılandırılacağını açıklar [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ve [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] dağıtmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="91a98-105">This topic describes how to configure [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>  
  
  
> [!NOTE]
>  <span data-ttu-id="91a98-106">Kontrol edebilirsiniz *UserAgent* bir sistemin sahip olup olmadığını belirlemek üzere kayıt defterini dizesinde [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] yüklü.</span><span class="sxs-lookup"><span data-stu-id="91a98-106">You can check the *UserAgent* string in the registry to determine whether a system has [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] installed.</span></span> <span data-ttu-id="91a98-107">Ayrıntıları ve inceler bir komut dosyası için *UserAgent* belirlemek için dize olup olmadığını [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] olan bir sistemde yüklü, [algılamak yüklü olup olmadığı .NET Framework 3.0](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="91a98-107">For details and a script that examines the *UserAgent* string to determine whether [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="91a98-108">İçerik sona erme ayarını ayarlama</span><span class="sxs-lookup"><span data-stu-id="91a98-108">Adjust the Content Expiration Setting</span></span>  
 <span data-ttu-id="91a98-109">İçerik sona erme ayarını 1 dakika ayarlamanız.</span><span class="sxs-lookup"><span data-stu-id="91a98-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="91a98-110">Aşağıdaki yordam ile bunun nasıl yapılacağı özetlenmektedir [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91a98-110">The following procedure outlines how to do this with [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span>  
  
1.  <span data-ttu-id="91a98-111">Tıklatın **Başlat** menüsündeki **Yönetimsel Araçlar**, tıklatıp **Internet Information Services (IIS) Yöneticisi'ni**.</span><span class="sxs-lookup"><span data-stu-id="91a98-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="91a98-112">Bu uygulama "% SystemRoot%\system32\inetsrv\iis.msc" ile komut satırından da başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91a98-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>  
  
2.  <span data-ttu-id="91a98-113">Genişletme [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] bulana kadar ağaç **varsayılan Web sitesi** düğümü.</span><span class="sxs-lookup"><span data-stu-id="91a98-113">Expand the [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] tree until you find the **Default Web site** node.</span></span>  
  
3.  <span data-ttu-id="91a98-114">Sağ **varsayılan Web sitesi** seçip **özellikleri** ve bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="91a98-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>  
  
4.  <span data-ttu-id="91a98-115">Seçin **HTTP üstbilgileri** sekmesinde ve "İçerik sona erme tarihini etkinleştir"'i tıklatın.</span><span class="sxs-lookup"><span data-stu-id="91a98-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>  
  
5.  <span data-ttu-id="91a98-116">İçeriğin 1 dakika sonra süresi dolacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="91a98-116">Set the content to expire after 1 minute.</span></span>  
  
<a name="register_mime_types"></a>   
## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="91a98-117">YAZMAÇ MIME türleri ve dosya uzantıları</span><span class="sxs-lookup"><span data-stu-id="91a98-117">Register MIME Types and File Extensions</span></span>  
 <span data-ttu-id="91a98-118">Birkaç kaydettirmelisiniz [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türlerini ve dosya uzantılarını böylece istemcinin sistemi üzerindeki tarayıcı doğru işleyiciyi yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="91a98-118">You must register several [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="91a98-119">Aşağıdaki türleri eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="91a98-119">You need to add the following types:</span></span>  
  
|<span data-ttu-id="91a98-120">Uzantısı</span><span class="sxs-lookup"><span data-stu-id="91a98-120">Extension</span></span>|<span data-ttu-id="91a98-121">MIME türü</span><span class="sxs-lookup"><span data-stu-id="91a98-121">MIME Type</span></span>|  
|---------------|---------------|  
|<span data-ttu-id="91a98-122">.manifest</span><span class="sxs-lookup"><span data-stu-id="91a98-122">.manifest</span></span>|<span data-ttu-id="91a98-123">Uygulama/bildirimi</span><span class="sxs-lookup"><span data-stu-id="91a98-123">application/manifest</span></span>|  
|<span data-ttu-id="91a98-124">.xaml</span><span class="sxs-lookup"><span data-stu-id="91a98-124">.xaml</span></span>|<span data-ttu-id="91a98-125">Uygulama/xaml + xml</span><span class="sxs-lookup"><span data-stu-id="91a98-125">application/xaml+xml</span></span>|  
|<span data-ttu-id="91a98-126">.Application</span><span class="sxs-lookup"><span data-stu-id="91a98-126">.application</span></span>|<span data-ttu-id="91a98-127">Uygulama/x-ms-uygulama</span><span class="sxs-lookup"><span data-stu-id="91a98-127">application/x-ms-application</span></span>|  
|<span data-ttu-id="91a98-128">.xbap</span><span class="sxs-lookup"><span data-stu-id="91a98-128">.xbap</span></span>|<span data-ttu-id="91a98-129">Uygulama/x-ms-xbap</span><span class="sxs-lookup"><span data-stu-id="91a98-129">application/x-ms-xbap</span></span>|  
|<span data-ttu-id="91a98-130">.deploy</span><span class="sxs-lookup"><span data-stu-id="91a98-130">.deploy</span></span>|<span data-ttu-id="91a98-131">application/octet-stream</span><span class="sxs-lookup"><span data-stu-id="91a98-131">application/octet-stream</span></span>|  
|<span data-ttu-id="91a98-132">.XPS</span><span class="sxs-lookup"><span data-stu-id="91a98-132">.xps</span></span>|<span data-ttu-id="91a98-133">Uygulama/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="91a98-133">application/vnd.ms-xpsdocument</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="91a98-134">Kaydetmeniz gerekmez [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türleri veya istemci sistemlerine dosya uzantıları.</span><span class="sxs-lookup"><span data-stu-id="91a98-134">You do not need to register [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types or file extensions on client systems.</span></span> <span data-ttu-id="91a98-135">Microsoft .NET Framework'ı yüklediğinizde otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="91a98-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>  
  
 <span data-ttu-id="91a98-136">Aşağıdaki Microsoft Visual Basic Scripting Edition (VBScript) örnek gerekli otomatik olarak ekler [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türlerine [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91a98-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types to [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span> <span data-ttu-id="91a98-137">Betik kullanmak için kodu sunucunuzdaki .vbs dosyasına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="91a98-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="91a98-138">Ardından, dosyayı komut satırından çalıştırma veya dosyayı çift komut dosyasını çalıştırmak [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91a98-138">Then, run the script by running the file from the command line or double-clicking the file in [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span></span>  
  
```  
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
  
' Get the mimemap object   
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
    Redim Preserve MimeMapArray(i)   
    Set MimeMapArray(i) = CreateObject("MimeMap")   
    MimeMapArray(i).Extension = Ext   
    MimeMapArray(i).MimeType = MType   
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray  
    MimeMapObj.SetInfo  
  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="91a98-139">Bu komut dosyası birden çok kez çalıştırarak birden çok oluşturur [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] eşleme girişi [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metatabanı.</span><span class="sxs-lookup"><span data-stu-id="91a98-139">Running this script multiple times creates multiple [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] map entries in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>  
  
 <span data-ttu-id="91a98-140">Bu komut dosyasını çalıştırdıktan sonra ek göremeyebilirsiniz [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] gelen türleri [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91a98-140">After you have run this script, you may not see additional [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types from the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span></span> <span data-ttu-id="91a98-141">Ancak, bunlar [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türleri eklenmiştir [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metatabanı.</span><span class="sxs-lookup"><span data-stu-id="91a98-141">However, these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types have been added to the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span> <span data-ttu-id="91a98-142">Aşağıdaki betiği tüm görüntüler [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türlerini [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metatabanı.</span><span class="sxs-lookup"><span data-stu-id="91a98-142">The following script will display all the [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>  
  
```  
' This script lists the MIME types for an IIS Server.  
' To use this script, just double-click or execute it from a command line   
' by calling cscript.exe  
  
dim mimeMapEntry, allMimeMaps  
  
' Get the mimemap object.  
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")  
allMimeMaps = mimeMapEntry.GetEx("MimeMap")  
  
' Display the mappings in the table.  
For Each mimeMap In allMimeMaps  
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")  
Next  
```  
  
 <span data-ttu-id="91a98-143">Komut dosyası olarak kaydetmek bir `.vbs` dosyası (örneğin, `DiscoverIISMimeTypes.vbs`) ve aşağıdaki komutu kullanarak komut isteminden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="91a98-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>  
  
 `cscript DiscoverIISMimeTypes.vbs`
