---
title: ServiceModel Kayıt Aracı (ServiceModelReg.exe)
description: Hizmet etkinleştirmesiyle ilgili sorunlar yaşıyorsanız, tek bir makineye WCF ve WF bileşenlerinin kaydedilmesini yönetmek için bu komut satırı aracını kullanın.
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 347b1b8071abe7d8eb7e16ffd879c1fdb9825bc7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245901"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="e8845-103">ServiceModel Kayıt Aracı (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="e8845-103">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="e8845-104">Bu komut satırı aracı, WCF ve WF bileşenlerinin tek bir makinede kaydını yönetme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8845-104">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="e8845-105">Normal koşullarda, WCF ve WF bileşenleri yüklendiğinde yapılandırıldığı için bu aracı kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e8845-105">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="e8845-106">Ancak hizmet etkinleştirme ile ilgili sorun yaşıyorsanız, bu aracı kullanarak bileşenleri kaydetmeyi deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8845-106">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8845-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e8845-107">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="e8845-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8845-108">Remarks</span></span>  
 <span data-ttu-id="e8845-109">Araç aşağıdaki konumda bulunabilir:</span><span class="sxs-lookup"><span data-stu-id="e8845-109">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="e8845-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="e8845-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="e8845-111">Windows Vista 'da ServiceModel Kayıt Aracı çalıştırıldığında, **Windows özellikleri** iletişim kutusu **Microsoft .NET Framework 3,0** altında **Windows Communication Foundation HTTP Etkinleştirme** seçeneğinin açık olduğunu yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e8845-111">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="e8845-112">**Windows özellikleri** Iletişim kutusuna **Başlat**' a ve ardından **Çalıştır** ' a tıklayıp **OptionalFeatures**yazarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e8845-112">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="e8845-113">Aşağıdaki tablolarda ServiceModelReg.exe ile kullanılabilecek seçenekler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e8845-113">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="e8845-114">Seçenek</span><span class="sxs-lookup"><span data-stu-id="e8845-114">Option</span></span>|<span data-ttu-id="e8845-115">Description</span><span class="sxs-lookup"><span data-stu-id="e8845-115">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="e8845-116">Tüm WCF ve WF bileşenlerini yükleme.</span><span class="sxs-lookup"><span data-stu-id="e8845-116">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="e8845-117">Tüm WCF ve WF bileşenlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e8845-117">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="e8845-118">Tüm WCF ve WF bileşenlerini onarır.</span><span class="sxs-lookup"><span data-stu-id="e8845-118">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="e8845-119">– C ile belirtilen WCF ve WF bileşenlerini yükleme.</span><span class="sxs-lookup"><span data-stu-id="e8845-119">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="e8845-120">– C ile belirtilen WCF ve WF bileşenlerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e8845-120">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="e8845-121">Bir bileşeni yüklüyor veya kaldırır:</span><span class="sxs-lookup"><span data-stu-id="e8845-121">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="e8845-122">-httpnamespace – HTTP ad alanı ayırma</span><span class="sxs-lookup"><span data-stu-id="e8845-122">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="e8845-123">-tcpportsharing – TCP bağlantı noktası paylaşım hizmeti</span><span class="sxs-lookup"><span data-stu-id="e8845-123">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="e8845-124">-tcpactivation – TCP etkinleştirme hizmeti (.NET 4 Istemci profilinde desteklenmez)</span><span class="sxs-lookup"><span data-stu-id="e8845-124">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="e8845-125">-namedpipeactivation-adlandırılmış kanal etkinleştirme hizmeti (.NET 4 Istemci profilinde desteklenmez</span><span class="sxs-lookup"><span data-stu-id="e8845-125">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="e8845-126">-MsmqActivation – MSMQ etkinleştirme hizmeti (.NET 4 Istemci profilinde desteklenmez</span><span class="sxs-lookup"><span data-stu-id="e8845-126">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="e8845-127">-ETW – ETW olay izleme bildirimleri (Windows Vista veya üzeri)</span><span class="sxs-lookup"><span data-stu-id="e8845-127">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="e8845-128">Sessiz mod (yalnızca hata günlüğünü görüntüle)</span><span class="sxs-lookup"><span data-stu-id="e8845-128">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="e8845-129">Ayrıntılı mod.</span><span class="sxs-lookup"><span data-stu-id="e8845-129">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="e8845-130">Telif hakkı ve başlık iletisini bastırır.</span><span class="sxs-lookup"><span data-stu-id="e8845-130">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="e8845-131">Yardım metnini görüntüler</span><span class="sxs-lookup"><span data-stu-id="e8845-131">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="e8845-132">FileLoadException hatası düzeltiliyor</span><span class="sxs-lookup"><span data-stu-id="e8845-132">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="e8845-133">Daha önceki WCF sürümlerini makinenize yüklediyseniz, `FileLoadFoundException` Yeni bir yükleme kaydetmek Için ServiceModelReg aracını çalıştırdığınızda bir hata alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8845-133">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="e8845-134">Bu, önceki yüklemeden dosyaları el ile kaldırmış olsanız bile bu durum oluşabilir, ancak machine.config ayarları değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="e8845-134">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="e8845-135">Hata iletisi aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="e8845-135">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="e8845-136">System. ServiceModel sürüm 2.0.0.0 derlemesinin erken bir müşteri teknolojisi Önizleme (CTP) sürümü tarafından yüklendiği hata iletisinden emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="e8845-136">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="e8845-137">System. ServiceModel derlemesinin geçerli sürümü bunun yerine 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="e8845-137">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="e8845-138">Bu nedenle, bir WCF 'nin ilk CTP sürümünün yüklendiği ancak tamamen kaldırılmadığı bir makineye resmi WCF sürümü yüklemek istediğinizde bu sorunla karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="e8845-138">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="e8845-139">ServiceModelReg.exe önceki sürüm girdilerini temizleyemiyor veya yeni sürümün girdilerini kaydedemezler.</span><span class="sxs-lookup"><span data-stu-id="e8845-139">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="e8845-140">Tek geçici çözüm machine.config el ile düzenlemedir. Bu dosyayı aşağıdaki konumda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8845-140">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="e8845-141">WCF 'yi 64 bitlik bir makinede çalıştırıyorsanız aynı dosyayı da bu konumda düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8845-141">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="e8845-142">Bu dosyadaki "System. ServiceModel, Version = 2.0.0.0" öğesine başvuran XML düğümlerini bulun, bunları ve tüm alt düğümleri silin.</span><span class="sxs-lookup"><span data-stu-id="e8845-142">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="e8845-143">Dosyayı kaydedin ve yeniden çalıştırın ServiceModelReg.exe bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="e8845-143">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e8845-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e8845-144">Examples</span></span>  
 <span data-ttu-id="e8845-145">Aşağıdaki örneklerde ServiceModelReg.exe aracının en yaygın seçeneklerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e8845-145">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
