---
title: WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 0a9cd5039c085f82f5507c93ebe0855cc620825d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916833"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="f4a01-102">WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="f4a01-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="f4a01-103">Workflow Services kayıt aracı (WFServicesReg. exe), Windows Workflow Foundation (WF) Hizmetleri için yapılandırma öğelerini eklemek, kaldırmak veya onarmak üzere kullanılabilecek tek başına bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="f4a01-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4a01-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4a01-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f4a01-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4a01-105">Remarks</span></span>  
 <span data-ttu-id="f4a01-106">Araç [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yükleme konumunda, özellikle,%windir%\Microsoft.NET\Framework\v3.5 veya 64 bitlik makinelerde bulunan%windir%\Microsoft.NET\Framework64\v3.5 adresinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f4a01-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="f4a01-107">Aşağıdaki tablolar, Iş akışı hizmetleri kayıt aracı (WFServicesReg. exe) ile kullanılabilen seçenekleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4a01-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="f4a01-108">Seçenek</span><span class="sxs-lookup"><span data-stu-id="f4a01-108">Option</span></span>|<span data-ttu-id="f4a01-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4a01-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="f4a01-110">Windows Workflow hizmetlerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f4a01-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="f4a01-111">Install ve Repair senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4a01-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="f4a01-112">Windows Workflow Services yapılandırmasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f4a01-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="f4a01-113">Ayrıntılı bilgileri yazdır (yapılandırma veya kaldırma için).</span><span class="sxs-lookup"><span data-stu-id="f4a01-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="f4a01-114">MSI günlük biçimini etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="f4a01-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="f4a01-115">Uygulama çalıştığında pencereyi en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="f4a01-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="f4a01-116">Kayıt</span><span class="sxs-lookup"><span data-stu-id="f4a01-116">Registration</span></span>  
 <span data-ttu-id="f4a01-117">Araç, Web. config dosyasını inceler ve aşağıdakileri kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f4a01-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<span data-ttu-id="f4a01-118">başvuru derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="f4a01-118">reference assemblies.</span></span>  
  
- <span data-ttu-id="f4a01-119">. Xoml dosyaları için derleme sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f4a01-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="f4a01-120">. Xoml ve. Rules dosyaları için HTTP işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="f4a01-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="f4a01-121">Araç, Machine. config dosyasını inceler ve aşağıdaki uzantıları kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f4a01-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="f4a01-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="f4a01-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="f4a01-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="f4a01-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="f4a01-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="f4a01-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="f4a01-125">Araç ayrıca aşağıdaki istemci meta veri içe aktarımlarını kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f4a01-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="f4a01-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="f4a01-126">policyImporters</span></span>  
  
- <span data-ttu-id="f4a01-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="f4a01-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="f4a01-128">Araç ayrıca. xoml ve. Rules komut dosyası eşleştirmelerini ve işleyicileri IIS metatabanında kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f4a01-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="f4a01-129">[!INCLUDE[ws2003](../../../includes/ws2003-md.md)] Ve[!INCLUDE[wxp](../../../includes/wxp-md.md)] makinelerinde (IIS 5,1 ve IIS 6,0), bir. xoml ve. Rules komut dosyası, bir kümesi kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f4a01-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="f4a01-130">64 bitlik makinelerde, `Enable32BitAppOnWin64` anahtar etkinse, araç, wow modu komut dosyası eşleştirmelerini veya `Enable32BitAppOnWin64` anahtar devre dışıysa yerel 64-bit komut dosyası eşleştirmelerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f4a01-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="f4a01-131">[!INCLUDE[wv](../../../includes/wv-md.md)] Ve Windows Server 2008 (IIS 7,0 ve üzeri) makineler, iki. xoml ve. Rules işleyicisi kümesi kaydedilir: biri tümleşik mod ve bir klasik mod için.</span><span class="sxs-lookup"><span data-stu-id="f4a01-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="f4a01-132">64 bit makinelerde, üç işleyici kümesi ( `Enable32BitAppOnWin64` anahtarın durumuna bakılmaksızın) kaydedilir: bir adet, bir tane, wow klasik mod ve diğeri yerel 64 bit klasik mod için bir adet tümleşik mod için.</span><span class="sxs-lookup"><span data-stu-id="f4a01-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4a01-133">ServiceModelreg. exe ' den farklı olarak, WFServicesReg. exe ' nin belirli bir Web sitesi için komut dosyası veya işleyicileri ekleme, kaldırma veya onarma izni yoktur.</span><span class="sxs-lookup"><span data-stu-id="f4a01-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="f4a01-134">Bu soruna geçici bir çözüm için, "komut dosyası eşleştirmelerini onarma" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f4a01-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="f4a01-135">Kullanım senaryoları</span><span class="sxs-lookup"><span data-stu-id="f4a01-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="f4a01-136">.NET Framework 3,5 yüklendikten sonra IIS yükleme</span><span class="sxs-lookup"><span data-stu-id="f4a01-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="f4a01-137">Bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makinede, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] IIS yüklemesinden önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f4a01-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="f4a01-138">IIS metatabanının KULLANILAMAMASINDAN dolayı, yüklemesi [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] . xoml ve. Rules komut dosyası yüklenmeden başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="f4a01-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="f4a01-139">IIS yüklendikten sonra, bu özel komut dosyası eşleştirmelerini yüklemek için WFServicesReg. exe aracını `/c` anahtarla birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4a01-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="f4a01-140">Kod haritalarını onarma</span><span class="sxs-lookup"><span data-stu-id="f4a01-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="f4a01-141">ScriptMap Web siteleri düğümü altında silindi</span><span class="sxs-lookup"><span data-stu-id="f4a01-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="f4a01-142">Bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makinede,. xoml veya. Rules, yanlışlıkla Web siteleri düğümünden silinir.</span><span class="sxs-lookup"><span data-stu-id="f4a01-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="f4a01-143">Bu, WFServicesReg. exe aracı `/c` anahtarıyla çalıştırılarak onarılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4a01-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="f4a01-144">ScriptMap belirli bir Web sitesi altında silindi</span><span class="sxs-lookup"><span data-stu-id="f4a01-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="f4a01-145">Bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makinede,. xoml veya. Rules, Web siteleri düğümünden değil, belirli bir Web sitesinden (örneğin, varsayılan Web sitesi) yanlışlıkla silinir.</span><span class="sxs-lookup"><span data-stu-id="f4a01-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="f4a01-146">Belirli bir Web sitesi için silinen işleyicileri onarmak üzere, tüm Web sitelerinden işleyicileri kaldırmak için "WFServicesReg. exe/r" komutunu çalıştırmanız ve sonra tüm Web siteleri için uygun işleyicileri oluşturmak üzere "WFServicesReg. exe/c" komutunu çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4a01-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="f4a01-147">IIS moduna geçtikten sonra işleyicileri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f4a01-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="f4a01-148">IIS paylaşılan yapılandırma modundayken ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yüklendiğinde, IIS metatabanı paylaşılan bir konum altında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f4a01-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="f4a01-149">IIS 'yi paylaşılmayan yapılandırma moduna geçerseniz, yerel metatabanı gerekli işleyicileri içermez.</span><span class="sxs-lookup"><span data-stu-id="f4a01-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="f4a01-150">Yerel metatabanını doğru şekilde yapılandırmak için, paylaşılan metatabanını yerel olarak içeri aktarabilir ya da yerel metatabanını yapılandıran "WFServicesReg. exe/c" komutunu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4a01-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
