---
title: "ServiceModel Kayıt Aracı (ServiceModelReg.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cfe522817fdc9a2aea23b1c9e8dce3b658d892c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="96d86-102">ServiceModel Kayıt Aracı (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="96d86-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="96d86-103">Bu komut satırı aracı, WCF ve WF bileşenleri tek bir makinede kaydını yönetme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="96d86-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="96d86-104">Normal koşullar altında WCF bu aracı kullanmak gerekmez ve WF bileşenler yüklendiğinde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="96d86-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="96d86-105">Ancak, hizmeti etkinleştirme ile ilgili sorunlar yaşıyor varsa, bu aracı kullanarak bileşenleri kaydetmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96d86-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96d86-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96d86-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="96d86-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96d86-107">Remarks</span></span>  
 <span data-ttu-id="96d86-108">Aracı şu konumda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="96d86-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="96d86-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows iletişim Foundation\\</span><span class="sxs-lookup"><span data-stu-id="96d86-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96d86-110">ServiceModel kayıt aracı çalıştırıldığında [!INCLUDE[wv](../../../includes/wv-md.md)], **Windows özelliklerini** iletişim değil yansıtmak, **Windows Communication Foundation HTTP etkinleştirmesi** seçeneği altında**Microsoft .NET Framework 3.0** açıktır.</span><span class="sxs-lookup"><span data-stu-id="96d86-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="96d86-111">**Windows özelliklerini** iletişim erişilebilir tıklayarak **Başlat**, ardından **çalıştırmak** yazarak **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="96d86-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="96d86-112">Aşağıdaki tablolarda ServiceModelReg.exe ile kullanılabilir seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96d86-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="96d86-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="96d86-113">Option</span></span>|<span data-ttu-id="96d86-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96d86-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="96d86-115">Tüm WCF ve WF bileşenleri yükler.</span><span class="sxs-lookup"><span data-stu-id="96d86-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="96d86-116">Tüm WCF ve WF bileşenleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="96d86-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="96d86-117">Tüm WCF ve WF bileşenleri onarır.</span><span class="sxs-lookup"><span data-stu-id="96d86-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="96d86-118">– C ile belirtilen WCF ve WF bileşenleri yükler.</span><span class="sxs-lookup"><span data-stu-id="96d86-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="96d86-119">– C ile belirtilen WCF ve WF bileşenleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="96d86-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="96d86-120">Yükler veya bir bileşen kaldırır:</span><span class="sxs-lookup"><span data-stu-id="96d86-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="96d86-121">-httpnamespace – HTTP Namespace ayırma</span><span class="sxs-lookup"><span data-stu-id="96d86-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="96d86-122">-tcpportsharing – TCP bağlantı noktası Paylaşımı hizmeti</span><span class="sxs-lookup"><span data-stu-id="96d86-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="96d86-123">-tcpactivation – TCP Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmeyen)</span><span class="sxs-lookup"><span data-stu-id="96d86-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="96d86-124">-namedpipeactivation – adlandırılmış kanal Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="96d86-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="96d86-125">-msmqactivation – MSMQ Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="96d86-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="96d86-126">-etw – ETW olay izleme bildirimleri (Windows Vista veya sonraki bir sürümü)</span><span class="sxs-lookup"><span data-stu-id="96d86-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="96d86-127">Sessiz mod (yalnızca görünen hata günlüğünü)</span><span class="sxs-lookup"><span data-stu-id="96d86-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="96d86-128">Ayrıntılı mod.</span><span class="sxs-lookup"><span data-stu-id="96d86-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="96d86-129">Telif hakkı ve başlık iletisi gizler.</span><span class="sxs-lookup"><span data-stu-id="96d86-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="96d86-130">Görüntüler Yardım metni</span><span class="sxs-lookup"><span data-stu-id="96d86-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="96d86-131">FileLoadException hata düzeltme</span><span class="sxs-lookup"><span data-stu-id="96d86-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="96d86-132">Önceki sürümlerini yüklediyseniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] , makinenizde alabilirsiniz bir `FileLoadFoundException` yeni bir yükleme kaydetmek için ServiceModelReg aracı'nı çalıştırdığınızda hata.</span><span class="sxs-lookup"><span data-stu-id="96d86-132">If you installed previous versions of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="96d86-133">El ile önceki yükle dosyaları kaldırıldı, ancak machine.config ayarları dokunulmadan olsa bile bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="96d86-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="96d86-134">Hata iletisi aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="96d86-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="96d86-135">System.ServiceModel 2.0.0.0 veya derleme yüklendi hata iletisinden unutmamalısınız erken bir müşteri teknolojisi Önizleme (CTP) sürümü tarafından.</span><span class="sxs-lookup"><span data-stu-id="96d86-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="96d86-136">Geçerli yayımlanan System.ServiceModel derleme 3.0.0.0 yerine sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="96d86-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="96d86-137">Resmi yüklemek istediğinizde bu nedenle, bu sorunu ile karşılaşıldı [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] burada erken bir CTP sürümünün bir makinede sürüm [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] yüklü, ancak tamamen kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="96d86-137">Therefore, this issue is encountered when you want to install the official [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] release on a machine where an early CTP release of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="96d86-138">Önceki sürüm girdilerini ServiceModelReg.exe temizleyemiyor ya da yeni sürümün girişleri kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96d86-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="96d86-139">Machine.config el ile düzenlemek için yalnızca geçici bir çözüm değildir. Bu dosya şu konumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96d86-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="96d86-140">Çalıştırıyorsanız, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 64-bit makine üzerinde Ayrıca aynı dosyanın bu konumda düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="96d86-140">If you are running [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="96d86-141">Başvurmak bu dosyadaki tüm XML düğümlerini bulun "System.ServiceModel, sürüm 2.0.0.0 =", bunları ve tüm alt düğümleri silin.</span><span class="sxs-lookup"><span data-stu-id="96d86-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="96d86-142">Dosyayı kaydedin ve ServiceModelReg.exe yeniden çalıştırmak bu sorunu giderir.</span><span class="sxs-lookup"><span data-stu-id="96d86-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="96d86-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="96d86-143">Examples</span></span>  
 <span data-ttu-id="96d86-144">Aşağıdaki örnekler ServiceModelReg.exe aracının en yaygın seçenekler kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="96d86-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
