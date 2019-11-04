---
title: ServiceModel Kayıt Aracı (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: aa9fc1b2338007db240fb10a9af35754107b07d0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424870"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="85235-102">ServiceModel Kayıt Aracı (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="85235-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="85235-103">Bu komut satırı aracı, WCF ve WF bileşenlerinin tek bir makinede kaydını yönetme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="85235-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="85235-104">Normal koşullarda, WCF ve WF bileşenleri yüklendiğinde yapılandırıldığı için bu aracı kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="85235-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="85235-105">Ancak hizmet etkinleştirme ile ilgili sorun yaşıyorsanız, bu aracı kullanarak bileşenleri kaydetmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85235-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85235-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85235-106">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="85235-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85235-107">Remarks</span></span>  
 <span data-ttu-id="85235-108">Araç aşağıdaki konumda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="85235-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="85235-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="85235-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="85235-110">[!INCLUDE[wv](../../../includes/wv-md.md)]üzerinde ServiceModel Kayıt Aracı çalıştırıldığında, **Windows özellikleri** iletişim kutusu **Microsoft .NET Framework 3,0** altında **Windows Communication Foundation HTTP Etkinleştirme** seçeneğinin açık olduğunu yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="85235-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="85235-111">**Windows özellikleri** Iletişim kutusuna **Başlat**' a ve ardından **Çalıştır** ' a tıklayıp **OptionalFeatures**yazarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="85235-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="85235-112">Aşağıdaki tablolar, ServiceModelReg. exe ile kullanılabilen seçenekleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85235-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="85235-113">Seçenek</span><span class="sxs-lookup"><span data-stu-id="85235-113">Option</span></span>|<span data-ttu-id="85235-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85235-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="85235-115">Tüm WCF ve WF bileşenlerini yükleme.</span><span class="sxs-lookup"><span data-stu-id="85235-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="85235-116">Tüm WCF ve WF bileşenlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="85235-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="85235-117">Tüm WCF ve WF bileşenlerini onarır.</span><span class="sxs-lookup"><span data-stu-id="85235-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="85235-118">– C ile belirtilen WCF ve WF bileşenlerini yükleme.</span><span class="sxs-lookup"><span data-stu-id="85235-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="85235-119">– C ile belirtilen WCF ve WF bileşenlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="85235-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="85235-120">Bir bileşeni yüklüyor veya kaldırır:</span><span class="sxs-lookup"><span data-stu-id="85235-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="85235-121">-httpnamespace – HTTP ad alanı ayırma</span><span class="sxs-lookup"><span data-stu-id="85235-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="85235-122">-tcpportsharing – TCP bağlantı noktası paylaşım hizmeti</span><span class="sxs-lookup"><span data-stu-id="85235-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="85235-123">-tcpactivation – TCP etkinleştirme hizmeti (.NET 4 Istemci profilinde desteklenmez)</span><span class="sxs-lookup"><span data-stu-id="85235-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="85235-124">-namedpipeactivation-adlandırılmış kanal etkinleştirme hizmeti (.NET 4 Istemci profilinde desteklenmez</span><span class="sxs-lookup"><span data-stu-id="85235-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="85235-125">-MsmqActivation – MSMQ etkinleştirme hizmeti (.NET 4 Istemci profilinde desteklenmez</span><span class="sxs-lookup"><span data-stu-id="85235-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="85235-126">-ETW – ETW olay izleme bildirimleri (Windows Vista veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="85235-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="85235-127">Sessiz mod (yalnızca hata günlüğünü görüntüle)</span><span class="sxs-lookup"><span data-stu-id="85235-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="85235-128">Ayrıntılı mod.</span><span class="sxs-lookup"><span data-stu-id="85235-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="85235-129">Telif hakkı ve başlık iletisini bastırır.</span><span class="sxs-lookup"><span data-stu-id="85235-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="85235-130">Yardım metnini görüntüler</span><span class="sxs-lookup"><span data-stu-id="85235-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="85235-131">FileLoadException hatası düzeltiliyor</span><span class="sxs-lookup"><span data-stu-id="85235-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="85235-132">Daha önceki WCF sürümlerini makinenize yüklediyseniz, yeni bir yükleme kaydetmek için ServiceModelReg aracını çalıştırdığınızda bir `FileLoadFoundException` hatası alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85235-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="85235-133">Bu, önceki yüklemeden dosyaları el ile kaldırmış olsanız, ancak Machine. config ayarlarından ayrılsanız bile gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="85235-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="85235-134">Hata iletisi aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="85235-134">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="85235-135">System. ServiceModel sürüm 2.0.0.0 derlemesinin erken bir müşteri teknolojisi Önizleme (CTP) sürümü tarafından yüklendiği hata iletisinden emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="85235-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="85235-136">System. ServiceModel derlemesinin geçerli sürümü bunun yerine 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="85235-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="85235-137">Bu nedenle, bir WCF 'nin ilk CTP sürümünün yüklendiği ancak tamamen kaldırılmadığı bir makineye resmi WCF sürümü yüklemek istediğinizde bu sorunla karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="85235-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="85235-138">ServiceModelReg. exe önceki sürüm girdilerini temizleyemiyor veya yeni sürümün girdilerini kaydedemezler.</span><span class="sxs-lookup"><span data-stu-id="85235-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="85235-139">Tek geçici çözüm, Machine. config dosyasını el ile düzenlemedir. Bu dosyayı aşağıdaki konumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85235-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="85235-140">WCF 'yi 64 bitlik bir makinede çalıştırıyorsanız aynı dosyayı da bu konumda düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="85235-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="85235-141">Bu dosyadaki "System. ServiceModel, Version = 2.0.0.0" öğesine başvuran XML düğümlerini bulun, bunları ve tüm alt düğümleri silin.</span><span class="sxs-lookup"><span data-stu-id="85235-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="85235-142">Dosyayı kaydedin ve ServiceModelReg. exe ' yi yeniden çalıştırın bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="85235-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="85235-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="85235-143">Examples</span></span>  
 <span data-ttu-id="85235-144">Aşağıdaki örneklerde ServiceModelReg. exe aracının en yaygın seçeneklerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85235-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
