---
title: WPF Konağı (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 88e4c6895039c84a57ed215a37a10a4b68851b2d
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817919"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="86ca1-102">WPF Konağı (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="86ca1-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="86ca1-103">Windows Presentation Foundation (WPF) ana bilgisayarı (PresentationHost. exe), uygulamaların uyumlu tarayıcılarda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] barındırılmasına olanak tanıyan uygulamadır (Microsoft Internet Explorer 6 ve üzeri dahil).</span><span class="sxs-lookup"><span data-stu-id="86ca1-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="86ca1-104">Varsayılan olarak, Windows Presentation Foundation (WPF) ana bilgisayarı, aşağıdakiler de dahil olmak [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] üzere tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içerik için kabuk ve işleyici olarak kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="86ca1-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
- <span data-ttu-id="86ca1-105">Gevşek (derlenmemiş) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyalar (. xaml).</span><span class="sxs-lookup"><span data-stu-id="86ca1-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]<span data-ttu-id="86ca1-106">(. XBAP).</span><span class="sxs-lookup"><span data-stu-id="86ca1-106">(.xbap).</span></span>  
  
 <span data-ttu-id="86ca1-107">Bu türlerin dosyaları için Windows Presentation Foundation (WPF) ana bilgisayarı:</span><span class="sxs-lookup"><span data-stu-id="86ca1-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="86ca1-108">Windows Presentation Foundation (WPF) içeriğini barındırmak için kayıtlı HTML işleyicisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="86ca1-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="86ca1-109">Gerekli ortak dil çalışma zamanı (CLR) ve Windows Presentation Foundation (WPF) derlemelerinin doğru sürümlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="86ca1-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="86ca1-110">Dağıtım bölgesi için uygun izin düzeylerinin yerinde olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="86ca1-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="86ca1-111">Bu konu, PresentationHost. exe ile kullanılabilecek komut satırı parametrelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="86ca1-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="86ca1-112">Kullanım</span><span class="sxs-lookup"><span data-stu-id="86ca1-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="86ca1-113">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86ca1-113">Parameters</span></span>  
  
|<span data-ttu-id="86ca1-114">Parametre</span><span class="sxs-lookup"><span data-stu-id="86ca1-114">Parameter</span></span>|<span data-ttu-id="86ca1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86ca1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86ca1-116">filename</span><span class="sxs-lookup"><span data-stu-id="86ca1-116">filename</span></span>|<span data-ttu-id="86ca1-117">Etkinleştirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="86ca1-117">The path of the file to be activated.</span></span> <span data-ttu-id="86ca1-118">Aynı zamanda bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]de olabilir.</span><span class="sxs-lookup"><span data-stu-id="86ca1-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="86ca1-119">-debug</span><span class="sxs-lookup"><span data-stu-id="86ca1-119">-debug</span></span>|<span data-ttu-id="86ca1-120">Bir uygulamayı etkinleştirirken, bir uygulamayı üzerinde yürütmez veya mağazadan çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="86ca1-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="86ca1-121">Bu yalnızca yerel bir dosya etkinleştirildiğinde işe yarar.</span><span class="sxs-lookup"><span data-stu-id="86ca1-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="86ca1-122">-DebugSecurityZoneURL \<URL 'si ></span><span class="sxs-lookup"><span data-stu-id="86ca1-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="86ca1-123">PresentationHost. exe [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] ' ye, bir uygulamanın, belirtilen [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]sunucudan dağıtılmışsa olarak hata ayıklaması gerektiğini belirten bir değerle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86ca1-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="86ca1-124">Bu hem dağıtım bölgesini hem de kaynak sitesini belirler.</span><span class="sxs-lookup"><span data-stu-id="86ca1-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="86ca1-125">-Gömme</span><span class="sxs-lookup"><span data-stu-id="86ca1-125">-embedding</span></span>|<span data-ttu-id="86ca1-126">OLE tarafından gerektirilir.</span><span class="sxs-lookup"><span data-stu-id="86ca1-126">Required by OLE.</span></span> <span data-ttu-id="86ca1-127">Ya da parametresi belirtilirse, bu parametre dahili olarak ayarlandığı için `-embedding` parametresini belirtmeniz gerekmez. `-debug` `-event`</span><span class="sxs-lookup"><span data-stu-id="86ca1-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="86ca1-128">-Event \<EventName ></span><span class="sxs-lookup"><span data-stu-id="86ca1-128">-event \<eventname></span></span>|<span data-ttu-id="86ca1-129">Bu adı taşıyan olayı açın ve PresentationHost. exe başlatıldığında ve içeriği barındırmak [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] için hazırsanız bunu işaret edin.</span><span class="sxs-lookup"><span data-stu-id="86ca1-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="86ca1-130">Olay açılırken bir hata oluşursa (örneğin, zaten oluşturulmadıysa) PresentationHost. exe sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="86ca1-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="86ca1-131">-launchApplication \<URL ></span><span class="sxs-lookup"><span data-stu-id="86ca1-131">-launchApplication \<url></span></span>|<span data-ttu-id="86ca1-132">Belirtilen URL 'den tek başına ClickOnce uygulaması başlatır.</span><span class="sxs-lookup"><span data-stu-id="86ca1-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="86ca1-133">.NET uygulamaları ile ilgili Internet Explorer ve WinINet güvenlik ilkesi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="86ca1-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="86ca1-134">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="86ca1-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="86ca1-135">Kabuk Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="86ca1-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="86ca1-136">MIME Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="86ca1-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="86ca1-137">Visual Studio hata ayıklaması</span><span class="sxs-lookup"><span data-stu-id="86ca1-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="86ca1-138">Bölgede Visual Studio hata ayıklaması</span><span class="sxs-lookup"><span data-stu-id="86ca1-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="86ca1-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86ca1-139">See also</span></span>

- [<span data-ttu-id="86ca1-140">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="86ca1-140">Security</span></span>](../security-wpf.md)
