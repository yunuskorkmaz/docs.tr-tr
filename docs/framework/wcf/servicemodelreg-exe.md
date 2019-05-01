---
title: ServiceModel Kayıt Aracı (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051799"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="ce3d0-102">ServiceModel Kayıt Aracı (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="ce3d0-103">Bu komut satırı aracı, WCF ve WF bileşenleri tek bir makinede kaydını yönetme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="ce3d0-104">Normal koşullar altında bu aracı WCF kullanın gerekmez ve WF bileşenler yüklendiğinde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="ce3d0-105">Ancak, hizmeti etkinleştirme ile ilgili sorunlar yaşıyorsanız, bu aracı kullanarak bileşenleri kaydetmek deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce3d0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce3d0-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ce3d0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce3d0-107">Remarks</span></span>  
 <span data-ttu-id="ce3d0-108">Aracı şu konumda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="ce3d0-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="ce3d0-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="ce3d0-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce3d0-110">ServiceModel kayıt aracı çalıştığında [!INCLUDE[wv](../../../includes/wv-md.md)], **Windows özellikleri** iletişim değil yansıtmak, **Windows Communication Foundation HTTP etkinleştirme** seçeneğinde**Microsoft .NET Framework 3.0** açıktır.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="ce3d0-111">**Windows özellikleri** tıklayarak iletişim erişilebilir **Başlat**, ardından **çalıştırma** ardından yazarak **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="ce3d0-112">Aşağıdaki tablolar ile ServiceModelReg.exe kullanılabilir seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="ce3d0-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="ce3d0-113">Option</span></span>|<span data-ttu-id="ce3d0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce3d0-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="ce3d0-115">WCF ve WF tüm bileşenlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="ce3d0-116">Tüm WCF ve WF bileşenleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="ce3d0-117">Tüm WCF ve WF bileşenleri onarır.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="ce3d0-118">– C ile belirtilen WCF ve WF bileşenlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="ce3d0-119">– C ile belirtilen WCF ve WF bileşenleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="ce3d0-120">Yükler veya bir bileşeni kaldırır:</span><span class="sxs-lookup"><span data-stu-id="ce3d0-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="ce3d0-121">-httpnamespace – HTTP Namespace ayırma</span><span class="sxs-lookup"><span data-stu-id="ce3d0-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="ce3d0-122">-tcpportsharing – TCP bağlantı noktası Paylaşım Hizmeti</span><span class="sxs-lookup"><span data-stu-id="ce3d0-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="ce3d0-123">-tcpactivation – TCP Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmez)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="ce3d0-124">-namedpipeactivation – adlandırılmış kanal etkinleştirmesi hizmet (.NET 4 istemci profili üzerinde desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="ce3d0-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="ce3d0-125">-msmqactivation – MSMQ Etkinleştirme Hizmeti (.NET 4 istemci profili üzerinde desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="ce3d0-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="ce3d0-126">-etw – ETW olay izleme bildirimleri (Windows Vista veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="ce3d0-127">Sessiz modu (yalnızca görünen hata günlüğü)</span><span class="sxs-lookup"><span data-stu-id="ce3d0-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="ce3d0-128">Ayrıntılı modu.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="ce3d0-129">Telif hakkı ve başlık iletisini bastırır.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="ce3d0-130">Yardım metni görüntüler</span><span class="sxs-lookup"><span data-stu-id="ce3d0-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="ce3d0-131">FileLoadException hata düzeltme</span><span class="sxs-lookup"><span data-stu-id="ce3d0-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="ce3d0-132">WCF'ın önceki sürümlerini makinenizde yüklü değilse, alabilirsiniz bir `FileLoadFoundException` yeni bir yükleme kaydedilecek ServiceModelReg aracı'nı çalıştırdığınızda hata.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="ce3d0-133">El ile dosyaları önceki yükle kaldırıldı ancak machine.config ayarları dokunulmadan olsa bile bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="ce3d0-134">Hata iletisi aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="ce3d0-135">System.ServiceModel sürüm 2.0.0.0 derleme yüklendiğini hata iletisindeki unutmamalısınız erken bir müşteri Technology Preview (CTP) sürümü tarafından.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="ce3d0-136">Geçerli yayımlanan System.ServiceModel derlemenin 3.0.0.0 yerine sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="ce3d0-137">Resmi WCF yayın burada WCF erken bir CTP sürümü yüklü, ancak tamamen kaldırılmış bir makineye yüklemek istediğinizde, bu nedenle, bu sorunla karşılaşılır.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="ce3d0-138">ServiceModelReg.exe önceki sürümünü girdilerin temizlenmesini olamaz ya da yeni sürümün girişleri kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="ce3d0-139">Machine.config el ile düzenlemek için yalnızca çözüm olabilir. Bu dosya şu konumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="ce3d0-140">WCF 64 bit makine üzerinde çalıştırıyorsanız, aynı dosyanın bu konumda da düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="ce3d0-141">Bu dosyadaki başvuran hiçbir XML düğümüyle bulun "System.ServiceModel, sürüm 2.0.0.0 =", bunları ve tüm alt düğümleri silin.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="ce3d0-142">Dosyayı kaydedin ve ServiceModelReg.exe yeniden çalıştırmak bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ce3d0-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ce3d0-143">Examples</span></span>  
 <span data-ttu-id="ce3d0-144">Aşağıdaki örnekler, en yaygın seçenekler ServiceModelReg.exe aracı kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce3d0-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
