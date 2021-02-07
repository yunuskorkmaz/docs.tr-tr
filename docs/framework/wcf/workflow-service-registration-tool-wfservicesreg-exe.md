---
description: 'Daha fazla bilgi edinin: Iş akışı hizmeti kayıt aracı (WFServicesReg.exe)'
title: WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 302da7e6e62db771472f95dc422cc7e97408600b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676332"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="f1e0a-103">WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="f1e0a-103">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>

<span data-ttu-id="f1e0a-104">Workflow Services kayıt aracı (WFServicesReg.exe), Windows Workflow Foundation (WF) Hizmetleri için yapılandırma öğelerini eklemek, kaldırmak veya onarmak üzere kullanılabilecek tek başına bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-104">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e0a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f1e0a-105">Syntax</span></span>  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f1e0a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1e0a-106">Remarks</span></span>  

 <span data-ttu-id="f1e0a-107">Araç .NET Framework 3,5 yükleme konumunda, özellikle,%windir%\Microsoft.NET\Framework\v3.5 veya 64 bit makinelerde bulunan%windir%\Microsoft.NET\Framework64\v3.5 adresinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-107">The tool can be found at the .NET Framework 3.5 installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="f1e0a-108">Aşağıdaki tablolar, Iş akışı hizmetleri kayıt aracı (WFServicesReg.exe) ile kullanılabilen seçenekleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-108">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="f1e0a-109">Seçenek</span><span class="sxs-lookup"><span data-stu-id="f1e0a-109">Option</span></span>|<span data-ttu-id="f1e0a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1e0a-110">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="f1e0a-111">Windows Workflow hizmetlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-111">Configures Windows Workflow Services.</span></span> <span data-ttu-id="f1e0a-112">Install ve Repair senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-112">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="f1e0a-113">Windows Workflow Services yapılandırmasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-113">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="f1e0a-114">Ayrıntılı bilgileri yazdır (yapılandırma veya kaldırma için).</span><span class="sxs-lookup"><span data-stu-id="f1e0a-114">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="f1e0a-115">MSI günlük biçimini etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-115">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="f1e0a-116">Uygulama çalıştığında pencereyi en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-116">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="f1e0a-117">Kayıt</span><span class="sxs-lookup"><span data-stu-id="f1e0a-117">Registration</span></span>  

 <span data-ttu-id="f1e0a-118">Araç Web.config dosyasını inceler ve aşağıdakileri kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f1e0a-118">The tool inspects the Web.config file and registers the following:</span></span>  
  
- <span data-ttu-id="f1e0a-119">.NET Framework 3,5 başvuru derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-119">.NET Framework 3.5 reference assemblies.</span></span>  
  
- <span data-ttu-id="f1e0a-120">. Xoml dosyaları için derleme sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-120">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="f1e0a-121">. Xoml ve. Rules dosyaları için HTTP işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-121">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="f1e0a-122">Araç Machine.config dosyasını inceler ve aşağıdaki uzantıları kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f1e0a-122">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="f1e0a-123">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="f1e0a-123">behaviorExtensions</span></span>  
  
- <span data-ttu-id="f1e0a-124">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="f1e0a-124">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="f1e0a-125">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="f1e0a-125">bindingExtensions</span></span>  
  
 <span data-ttu-id="f1e0a-126">Araç ayrıca aşağıdaki istemci meta veri içe aktarımlarını kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f1e0a-126">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="f1e0a-127">policyImporters</span><span class="sxs-lookup"><span data-stu-id="f1e0a-127">policyImporters</span></span>  
  
- <span data-ttu-id="f1e0a-128">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="f1e0a-128">wsdlImporters</span></span>  
  
 <span data-ttu-id="f1e0a-129">Araç ayrıca. xoml ve. Rules komut dosyası eşleştirmelerini ve işleyicileri IIS metatabanında kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-129">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="f1e0a-130">Windows Server 2003 ve Windows XP makinelerinde (IIS 5,1 ve IIS 6,0), bir. xoml ve. Rules komut dosyası, bir kümesi kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-130">On Windows Server 2003 and Windows XP machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="f1e0a-131">64 bitlik makinelerde, anahtar etkinse, araç, WOW modu komut dosyası eşleştirmelerini `Enable32BitAppOnWin64` veya anahtar devre dışıysa yerel 64-bit komut dosyası eşleştirmelerini kaydeder `Enable32BitAppOnWin64` .</span><span class="sxs-lookup"><span data-stu-id="f1e0a-131">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="f1e0a-132">Windows Vista ve Windows Server 2008 (IIS 7,0 ve üzeri) makinelerinde, iki. xoml ve. Rules işleyicisi kümesi kaydedilir: biri tümleşik mod ve bir klasik mod için.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-132">On Windows Vista and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="f1e0a-133">64 bit makinelerde, üç işleyici kümesi (anahtarın durumuna bakılmaksızın) kaydedilir: bir adet, bir tane `Enable32BitAppOnWin64` , wow klasik mod ve diğeri yerel 64 bit klasik mod için bir adet tümleşik mod için.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-133">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1e0a-134">ServiceModelreg.exe farklı olarak, WFServicesReg.exe belirli bir Web sitesi için komut dosyası veya işleyicileri ekleme, kaldırma veya onarmaya izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-134">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="f1e0a-135">Bu soruna geçici bir çözüm için, "komut dosyası eşleştirmelerini onarma" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-135">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="f1e0a-136">Kullanım senaryoları</span><span class="sxs-lookup"><span data-stu-id="f1e0a-136">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="f1e0a-137">.NET Framework 3,5 yüklendikten sonra IIS yükleme</span><span class="sxs-lookup"><span data-stu-id="f1e0a-137">Installing IIS after .NET Framework 3.5 is installed</span></span>  

 <span data-ttu-id="f1e0a-138">Windows Server 2003 makinesinde, IIS yüklemesinden önce .NET Framework 3,5 yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-138">On a Windows Server 2003 machine, .NET Framework 3.5 is installed prior to IIS installation.</span></span> <span data-ttu-id="f1e0a-139">IIS metatabanının KULLANILAMAMASINDAN dolayı, .NET Framework 3,5 yüklemesi. xoml ve. Rules komut dosyası yüklemeleri olmadan başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-139">Due to the unavailability of the IIS metabase, installation of .NET Framework 3.5 succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="f1e0a-140">IIS yüklendikten sonra, `/c` Bu özel komut dosyası eşleştirmelerini yüklemek için WFServicesReg.exe aracını anahtarla birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-140">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="f1e0a-141">Kod haritalarını onarma</span><span class="sxs-lookup"><span data-stu-id="f1e0a-141">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="f1e0a-142">ScriptMap Web siteleri düğümü altında silindi</span><span class="sxs-lookup"><span data-stu-id="f1e0a-142">Scriptmap deleted under Web Sites node</span></span>  

 <span data-ttu-id="f1e0a-143">Bir Windows Server 2003 makinesinde,. xoml veya. Rules, yanlışlıkla Web siteleri düğümünden silinir.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-143">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="f1e0a-144">Bu, anahtarla WFServicesReg.exe aracı çalıştırılarak onarılabilir `/c` .</span><span class="sxs-lookup"><span data-stu-id="f1e0a-144">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="f1e0a-145">ScriptMap belirli bir Web sitesi altında silindi</span><span class="sxs-lookup"><span data-stu-id="f1e0a-145">Scriptmap deleted under a particular Web site</span></span>  

 <span data-ttu-id="f1e0a-146">Bir Windows Server 2003 makinesinde,. xoml veya. Rules, Web siteleri düğümünden değil, belirli bir Web sitesinden (örneğin, varsayılan Web sitesi) yanlışlıkla silinir.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-146">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="f1e0a-147">Belirli bir Web sitesi için silinen işleyicileri onarmak üzere, tüm Web sitelerinden işleyicileri kaldırmak için "WFServicesReg.exe/r" çalıştırmanız gerekir, sonra tüm Web siteleri için uygun işleyicileri oluşturmak için "WFServicesReg.exe/c" öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-147">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="f1e0a-148">IIS moduna geçtikten sonra işleyicileri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f1e0a-148">Configuring handlers after switching IIS mode</span></span>  

 <span data-ttu-id="f1e0a-149">IIS paylaşılan yapılandırma modundayken ve 3,5 .NET Framework yüklüyse, IIS metatabanı paylaşılan bir konum altında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-149">When IIS is in shared configuration mode and .NET Framework 3.5 is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="f1e0a-150">IIS 'yi paylaşılmayan yapılandırma moduna geçerseniz, yerel metatabanı gerekli işleyicileri içermez.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-150">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="f1e0a-151">Yerel metatabanını doğru şekilde yapılandırmak için, paylaşılan metatabanını yerel olarak içeri aktarabilir veya yerel metatabanını yapılandıran "WFServicesReg.exe/c" öğesini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1e0a-151">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
