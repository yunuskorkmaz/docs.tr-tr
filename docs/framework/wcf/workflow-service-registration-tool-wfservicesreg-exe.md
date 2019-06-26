---
title: WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 211af75c04dfe971228bc1710fbe1fc4d7aaee60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402477"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="1b603-102">WorkFlow Hizmet Kayıt Aracı (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="1b603-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="1b603-103">Workflow hizmet Kayıt Aracı (WFServicesReg.exe) eklemek, kaldırmak veya Windows Workflow Foundation (WF) Hizmetleri için yapılandırma öğeleri onarmak için kullanılan bağımsız bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="1b603-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b603-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b603-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="1b603-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b603-105">Remarks</span></span>  
 <span data-ttu-id="1b603-106">Araç şu yolda bulunabilir: [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] yükleme konumu, özellikle de % windir%\Microsoft.NET\Framework\v3.5 veya 64 bit makinelerde %windir%\Microsoft.NET\Framework64\v3.5.</span><span class="sxs-lookup"><span data-stu-id="1b603-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="1b603-107">Aşağıdaki tablolarda, iş akışı hizmetleri kayıt aracı (WFServicesReg.exe) kullanılabilir seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b603-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="1b603-108">Seçenek</span><span class="sxs-lookup"><span data-stu-id="1b603-108">Option</span></span>|<span data-ttu-id="1b603-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b603-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="1b603-110">Windows iş akışı hizmetleri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1b603-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="1b603-111">Yüklemede kullanılan ve onarım senaryoları.</span><span class="sxs-lookup"><span data-stu-id="1b603-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="1b603-112">Windows iş akışı Hizmetleri yapılandırmasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1b603-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="1b603-113">Ayrıntılı bilgi (yapılandırma veya temizleme) yazdırın.</span><span class="sxs-lookup"><span data-stu-id="1b603-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="1b603-114">MSI günlük biçimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b603-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="1b603-115">Uygulama çalışırken pencerenin en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="1b603-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="1b603-116">Kayıt</span><span class="sxs-lookup"><span data-stu-id="1b603-116">Registration</span></span>  
 <span data-ttu-id="1b603-117">Araç, Web.config dosyasını inceler ve aşağıdaki kaydeder:</span><span class="sxs-lookup"><span data-stu-id="1b603-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <span data-ttu-id="1b603-118">başvuru bütünleştirilmiş kodları.</span><span class="sxs-lookup"><span data-stu-id="1b603-118">reference assemblies.</span></span>  
  
- <span data-ttu-id="1b603-119">Bir oluşturma sağlayıcısını .xoml dosyaları.</span><span class="sxs-lookup"><span data-stu-id="1b603-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="1b603-120">HTTP işleyicileri .xoml ve .rules dosyaları.</span><span class="sxs-lookup"><span data-stu-id="1b603-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="1b603-121">Aracı Machine.config dosyasının inceler ve aşağıdaki uzantılar kaydeder:</span><span class="sxs-lookup"><span data-stu-id="1b603-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="1b603-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="1b603-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="1b603-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="1b603-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="1b603-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="1b603-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="1b603-125">Araç ayrıca aşağıdaki istemci meta verileri ımporters kaydeder:</span><span class="sxs-lookup"><span data-stu-id="1b603-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="1b603-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="1b603-126">policyImporters</span></span>  
  
- <span data-ttu-id="1b603-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="1b603-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="1b603-128">Aracı, IIS metabase içinde .xoml ve .rules kod haritalarını ve işleyicileri de kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1b603-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="1b603-129">Üzerinde [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../includes/wxp-md.md)] makineler .xoml ve .rules kod haritalarını (IIS 5.1 ve IIS 6.0), bir dizi kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="1b603-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="1b603-130">64 bit makinelerde ise araç WOW modunda kod haritalarını kaydeder `Enable32BitAppOnWin64` anahtar etkin veya yerel 64 bit kod haritalarını olup olmadığını `Enable32BitAppOnWin64` anahtarını devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="1b603-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="1b603-131">Üzerinde [!INCLUDE[wv](../../../includes/wv-md.md)] ve Windows Server 2008 (IIS 7.0 ve üstü) makineleri iki .xoml ve .rules işleyicileri kayıtlı: biri tümleşik modu, diğeri Klasik mod için.</span><span class="sxs-lookup"><span data-stu-id="1b603-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="1b603-132">64 bit makinelerde işleyicileri üç adet kaydedilir (durumundan bağımsız olarak `Enable32BitAppOnWin64` geçiş): bir tümleşik modu, WOW Klasik mod için ve yerel 64 bit Klasik mod için bir tane.</span><span class="sxs-lookup"><span data-stu-id="1b603-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b603-133">ServiceModelreg.exe WFServicesReg.exe ekleme, kaldırma veya kod haritalarını veya belirli bir Web sitesi için işleyiciler onarma izin vermez.</span><span class="sxs-lookup"><span data-stu-id="1b603-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="1b603-134">Bu soruna bir geçici çözüm için "Kod haritalarını onarma" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1b603-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="1b603-135">Kullanım senaryoları</span><span class="sxs-lookup"><span data-stu-id="1b603-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="1b603-136">.NET Framework 3.5 yüklendikten sonra IIS yükleme</span><span class="sxs-lookup"><span data-stu-id="1b603-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="1b603-137">Üzerinde bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makine [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] IIS yüklemeden önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1b603-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="1b603-138">IIS metatabanı yüklenmesini olmadığından [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] .xoml ve .rules kod haritalarını yüklemeden başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="1b603-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="1b603-139">IIS yüklendikten sonra WFServicesReg.exe aracı ile kullanabileceğiniz `/c` bu belirli kod haritalarını yüklemek için anahtar.</span><span class="sxs-lookup"><span data-stu-id="1b603-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="1b603-140">Kod haritalarını onarılıyor</span><span class="sxs-lookup"><span data-stu-id="1b603-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="1b603-141">Komut dosyası eşlemesini Web siteleri düğümü altında silindi</span><span class="sxs-lookup"><span data-stu-id="1b603-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="1b603-142">Üzerinde bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makine, .xoml veya .rules Web siteleri düğümünden silinmiş yanlışlıkla.</span><span class="sxs-lookup"><span data-stu-id="1b603-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="1b603-143">Bu WFServicesReg.exe aracıyla çalıştırarak onarılabilir `/c` geçin.</span><span class="sxs-lookup"><span data-stu-id="1b603-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="1b603-144">Komut dosyası eşlemesini altında belirli bir Web sitesi silindi</span><span class="sxs-lookup"><span data-stu-id="1b603-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="1b603-145">Üzerinde bir [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] makine, .xoml veya .rules yanlışlıkla silindiğinde belirli bir Web sitesi (örneğin, varsayılan Web sitesi) yerine Web siteleri düğümü.</span><span class="sxs-lookup"><span data-stu-id="1b603-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="1b603-146">Belirli bir Web sitesi için silinen işleyicileri onarmak için "WFServicesReg.exe r" çalıştırmalısınız tüm Web sitelerinden işleyicilerini kaldırmak için ardından "WFServicesReg.exe c" çalıştırın uygun işleyicileri için tüm Web siteleri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1b603-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="1b603-147">IIS moduna geçtikten sonra işleyicileri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1b603-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="1b603-148">IIS paylaşılan Yapılandırması modunda olduğunda ve [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] olan yüklü IIS metabase bir paylaşılan konuma altında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="1b603-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="1b603-149">IIS yapılandırma paylaşılmayan moduna geçiş yapıyorsanız, yerel gerekli işleyicileri içermez.</span><span class="sxs-lookup"><span data-stu-id="1b603-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="1b603-150">Yerel düzgün şekilde yapılandırmak için "yerel yapılandıran yerel ya da çalışma WFServicesReg.exe /c", paylaşılan metatabanına ya da içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b603-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
