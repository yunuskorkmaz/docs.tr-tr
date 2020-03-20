---
title: ServiceModel Kayıt Aracı (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183103"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="78f2f-102">ServiceModel Kayıt Aracı (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="78f2f-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="78f2f-103">Bu komut satırı aracı, WCF ve WF bileşenlerinin tek bir makinede kaydını yönetme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="78f2f-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="78f2f-104">Normal koşullarda, wcf ve WF bileşenleri yüklendiğinde yapılandırıldığından bu aracı kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="78f2f-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="78f2f-105">Ancak hizmet etkinleştirme yle ilgili sorunlar yaşıyorsanız, bileşenleri bu aracı kullanarak kaydetmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78f2f-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f2f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78f2f-106">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="78f2f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78f2f-107">Remarks</span></span>  
 <span data-ttu-id="78f2f-108">Araç aşağıdaki konumda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="78f2f-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="78f2f-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="78f2f-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="78f2f-110">ServiceModel Kayıt Aracı Windows Vista'da çalıştırıldığında, **Windows Özellikleri** iletişim kutusu **Microsoft .NET Framework 3.0** altındaki **Windows Communication Foundation HTTP Etkinleştirme** seçeneğinin açık olduğunu yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="78f2f-110">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="78f2f-111">**Windows Özellikleri** iletişim kutusuna **Başlat'ı**tıklatarak erişilebilir, ardından **Çalıştır'ı** tıklatın ve ardından **İsteğe Bağlı Özellikler**yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78f2f-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="78f2f-112">Aşağıdaki tablolar ServiceModelReg.exe ile kullanılabilecek seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="78f2f-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="78f2f-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="78f2f-113">Option</span></span>|<span data-ttu-id="78f2f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78f2f-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="78f2f-115">Tüm WCF ve WF bileşenlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="78f2f-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="78f2f-116">Tüm WCF ve WF bileşenlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="78f2f-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="78f2f-117">Tüm WCF ve WF bileşenlerini onarır.</span><span class="sxs-lookup"><span data-stu-id="78f2f-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="78f2f-118">–c ile belirtilen WCF ve WF bileşenlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="78f2f-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="78f2f-119">–c ile belirtilen WCF ve WF bileşenlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="78f2f-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="78f2f-120">Bir bileşeni yükler veya yükler:</span><span class="sxs-lookup"><span data-stu-id="78f2f-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="78f2f-121">- httpnamespace – HTTP Namespace Rezervasyon</span><span class="sxs-lookup"><span data-stu-id="78f2f-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="78f2f-122">- tcpportsharing – TCP port paylaşım hizmeti</span><span class="sxs-lookup"><span data-stu-id="78f2f-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="78f2f-123">- tcpactivation – TCP aktivasyon hizmeti (.NET 4 İstemci Profili'nde desteklenmez)</span><span class="sxs-lookup"><span data-stu-id="78f2f-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="78f2f-124">- namedpipeactivation – Named pipe aktivasyon hizmeti (.NET 4 İstemci Profilinde desteklenmez</span><span class="sxs-lookup"><span data-stu-id="78f2f-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="78f2f-125">- msmqactivation – MSMQ aktivasyon hizmeti (.NET 4 İstemci Profilinde desteklenmez</span><span class="sxs-lookup"><span data-stu-id="78f2f-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="78f2f-126">- etw - ETW olay izleme manifestoları (Windows Vista veya daha sonra)</span><span class="sxs-lookup"><span data-stu-id="78f2f-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="78f2f-127">Sessiz mod (yalnızca hata günlüğe kaydetme)</span><span class="sxs-lookup"><span data-stu-id="78f2f-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="78f2f-128">Verbose modu.</span><span class="sxs-lookup"><span data-stu-id="78f2f-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="78f2f-129">Telif hakkı ve banner mesajını bastırır.</span><span class="sxs-lookup"><span data-stu-id="78f2f-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="78f2f-130">Yardım metnini görüntüler</span><span class="sxs-lookup"><span data-stu-id="78f2f-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="78f2f-131">FileLoadException Hatası düzeltme</span><span class="sxs-lookup"><span data-stu-id="78f2f-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="78f2f-132">Makinenize WCF'nin önceki sürümlerini yüklediyseniz, `FileLoadFoundException` yeni bir yükleme kaydetmek için ServiceModelReg aracını çalıştırdığınızda bir hata alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78f2f-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="78f2f-133">Bu, önceki yüklemeden dosyaları el ile kaldırdınız, ancak machine.config ayarlarını sağlam bıraksanız bile gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="78f2f-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="78f2f-134">Hata iletisi aşağıdakilere benzer.</span><span class="sxs-lookup"><span data-stu-id="78f2f-134">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="78f2f-135">System.ServiceModel Version 2.0.0.0 derlemesinin erken bir Müşteri Teknolojisi Önizleme (CTP) sürümü tarafından yüklenmiş olduğunu hata iletisinden not almalısınız.</span><span class="sxs-lookup"><span data-stu-id="78f2f-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="78f2f-136">Yayımlanan System.ServiceModel derlemesinin geçerli sürümü 3.0.0.0 yerine.</span><span class="sxs-lookup"><span data-stu-id="78f2f-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="78f2f-137">Bu nedenle, resmi WCF sürümü wcf erken CTP sürümü yüklü olduğu bir makineye yüklemek istediğinizde bu sorunla karşılaşılan, ancak tamamen kaldırıldı değil.</span><span class="sxs-lookup"><span data-stu-id="78f2f-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="78f2f-138">ServiceModelReg.exe önceki sürüm girişlerini temizleyemez ve yeni sürümün girişlerini kaydedemez.</span><span class="sxs-lookup"><span data-stu-id="78f2f-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="78f2f-139">Tek geçici çözüm, machine.config'i el ile düzenliyor. Bu dosyayı aşağıdaki konumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78f2f-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="78f2f-140">WCF'yi 64 bit makinede çalıştırıyorsanız, aynı dosyayı bu konumda da değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="78f2f-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="78f2f-141">Bu dosyada "System.ServiceModel, Version=2.0.0.0" anlamına gelen XML düğümlerini bulun, bunları ve alt düğümleri silin.</span><span class="sxs-lookup"><span data-stu-id="78f2f-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="78f2f-142">Dosyayı kaydedin ve ServiceModelReg.exe'yi yeniden çalıştırın bu sorunu giderir.</span><span class="sxs-lookup"><span data-stu-id="78f2f-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="78f2f-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="78f2f-143">Examples</span></span>  
 <span data-ttu-id="78f2f-144">Aşağıdaki örnekler serviceModelReg.exe aracının en yaygın seçeneklerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78f2f-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
