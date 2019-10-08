---
title: WPF Konağı (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: c1c26b49a33a58189f66e7b938333f362e467853
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002157"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="e39af-102">WPF Konağı (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e39af-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="e39af-103">Windows Presentation Foundation (WPF) ana bilgisayarı (PresentationHost. exe), [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalarının uyumlu tarayıcılarda barındırılmasına olanak tanıyan uygulamadır (Microsoft Internet Explorer 6 ve üzeri dahil).</span><span class="sxs-lookup"><span data-stu-id="e39af-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="e39af-104">Varsayılan olarak, Windows Presentation Foundation (WPF) ana bilgisayarı, tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriği için kabuk ve MIME işleyicisi olarak kaydedilir ve şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="e39af-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
- <span data-ttu-id="e39af-105">Gevşek (derlenmemiş) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya (. xaml).</span><span class="sxs-lookup"><span data-stu-id="e39af-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] <span data-ttu-id="e39af-106">(. XBAP).</span><span class="sxs-lookup"><span data-stu-id="e39af-106">(.xbap).</span></span>  
  
 <span data-ttu-id="e39af-107">Bu türlerin dosyaları için Windows Presentation Foundation (WPF) ana bilgisayarı:</span><span class="sxs-lookup"><span data-stu-id="e39af-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="e39af-108">Windows Presentation Foundation (WPF) içeriğini barındırmak için kayıtlı HTML işleyicisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="e39af-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="e39af-109">Gerekli ortak dil çalışma zamanı (CLR) ve Windows Presentation Foundation (WPF) derlemelerinin doğru sürümlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="e39af-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="e39af-110">Dağıtım bölgesi için uygun izin düzeylerinin yerinde olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e39af-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="e39af-111">Bu konu, PresentationHost. exe ile kullanılabilecek komut satırı parametrelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e39af-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e39af-112">Kullanım</span><span class="sxs-lookup"><span data-stu-id="e39af-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="e39af-113">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e39af-113">Parameters</span></span>  
  
|<span data-ttu-id="e39af-114">Parametre</span><span class="sxs-lookup"><span data-stu-id="e39af-114">Parameter</span></span>|<span data-ttu-id="e39af-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e39af-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e39af-116">filename</span><span class="sxs-lookup"><span data-stu-id="e39af-116">filename</span></span>|<span data-ttu-id="e39af-117">Etkinleştirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="e39af-117">The path of the file to be activated.</span></span> <span data-ttu-id="e39af-118">Ayrıca bir @no__t olabilir.</span><span class="sxs-lookup"><span data-stu-id="e39af-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="e39af-119">-debug</span><span class="sxs-lookup"><span data-stu-id="e39af-119">-debug</span></span>|<span data-ttu-id="e39af-120">Bir uygulamayı etkinleştirirken, bir uygulamayı üzerinde yürütmez veya mağazadan çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="e39af-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="e39af-121">Bu yalnızca yerel bir dosya etkinleştirildiğinde işe yarar.</span><span class="sxs-lookup"><span data-stu-id="e39af-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="e39af-122">-debugSecurityZoneURL \<url ></span><span class="sxs-lookup"><span data-stu-id="e39af-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="e39af-123">Bir uygulamanın, belirtilen URL 'den dağıtılarak hata ayıklaması gerektiğini PresentationHost. exe ' ye işaret eden bir URL değeriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e39af-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="e39af-124">Bu hem dağıtım bölgesini hem de kaynak sitesini belirler.</span><span class="sxs-lookup"><span data-stu-id="e39af-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="e39af-125">-Gömme</span><span class="sxs-lookup"><span data-stu-id="e39af-125">-embedding</span></span>|<span data-ttu-id="e39af-126">OLE tarafından gerektirilir.</span><span class="sxs-lookup"><span data-stu-id="e39af-126">Required by OLE.</span></span> <span data-ttu-id="e39af-127">@No__t-0 veya `-debug` parametresi belirtilirse, bu parametre dahili olarak ayarlandığı için `-embedding` parametresini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e39af-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="e39af-128">-Event \<eventname ></span><span class="sxs-lookup"><span data-stu-id="e39af-128">-event \<eventname></span></span>|<span data-ttu-id="e39af-129">Bu adı taşıyan olayı açın ve PresentationHost. exe başlatıldığında ve [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriğini barındırmak için hazırsanız bunu işaret edin.</span><span class="sxs-lookup"><span data-stu-id="e39af-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="e39af-130">Olay açılırken bir hata oluşursa (örneğin, zaten oluşturulmadıysa) PresentationHost. exe sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e39af-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="e39af-131">-launchApplication \<url ></span><span class="sxs-lookup"><span data-stu-id="e39af-131">-launchApplication \<url></span></span>|<span data-ttu-id="e39af-132">Belirtilen URL 'den tek başına ClickOnce uygulaması başlatır.</span><span class="sxs-lookup"><span data-stu-id="e39af-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="e39af-133">.NET uygulamaları ile ilgili Internet Explorer ve WinINet güvenlik ilkesi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e39af-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="e39af-134">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="e39af-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="e39af-135">Kabuk Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="e39af-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="e39af-136">MIME Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="e39af-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="e39af-137">Visual Studio hata ayıklaması</span><span class="sxs-lookup"><span data-stu-id="e39af-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="e39af-138">Bölgede Visual Studio hata ayıklaması</span><span class="sxs-lookup"><span data-stu-id="e39af-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="e39af-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e39af-139">See also</span></span>

- [<span data-ttu-id="e39af-140">Security</span><span class="sxs-lookup"><span data-stu-id="e39af-140">Security</span></span>](../security-wpf.md)
