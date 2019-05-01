---
title: WPF Konağı (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 586d306d0f375241c9382e1e24cf1af75b990ba9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019171"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="ae1f7-102">WPF Konağı (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="ae1f7-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="ae1f7-103">Windows Presentation Foundation (WPF) Konağı (PresentationHost.exe) sağlayan bir uygulama olan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uyumlu tarayıcılarda uygulamaları (dahil olmak üzere [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="ae1f7-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="ae1f7-104">Varsayılan olarak, Windows Presentation Foundation (WPF) konak olarak kabuğa kayıtlı ve [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] işleyicisi için tarayıcıda barındırılan [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriği olarak da içerir:</span><span class="sxs-lookup"><span data-stu-id="ae1f7-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
- <span data-ttu-id="ae1f7-105">Gevşek (derlenmemiş) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları (.xaml).</span><span class="sxs-lookup"><span data-stu-id="ae1f7-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] <span data-ttu-id="ae1f7-106">(.xbap).</span><span class="sxs-lookup"><span data-stu-id="ae1f7-106">(.xbap).</span></span>  
  
 <span data-ttu-id="ae1f7-107">Bu tür dosyalar için Windows Presentation Foundation (WPF) ana bilgisayar için:</span><span class="sxs-lookup"><span data-stu-id="ae1f7-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="ae1f7-108">Kayıtlı başlatır [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] Windows Presentation Foundation (WPF) içeriğini barındırmak için işleyici.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="ae1f7-109">Gerekli doğru sürümlerini yükler [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] ve Windows Presentation Foundation (WPF) derlemeleri.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-109">Loads the right versions of the required [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="ae1f7-110">Dağıtım bölgesi için uygun izin düzeylerini yerinde olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="ae1f7-111">Bu konu ile PresentationHost.exe kullanılabilir komut satırı parametreleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="ae1f7-112">Kullanım</span><span class="sxs-lookup"><span data-stu-id="ae1f7-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="ae1f7-113">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae1f7-113">Parameters</span></span>  
  
|<span data-ttu-id="ae1f7-114">Parametre</span><span class="sxs-lookup"><span data-stu-id="ae1f7-114">Parameter</span></span>|<span data-ttu-id="ae1f7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae1f7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae1f7-116">filename</span><span class="sxs-lookup"><span data-stu-id="ae1f7-116">filename</span></span>|<span data-ttu-id="ae1f7-117">Etkinleştirilecek dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-117">The path of the file to be activated.</span></span> <span data-ttu-id="ae1f7-118">Ayrıca olabilir bir [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae1f7-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="ae1f7-119">-debug</span><span class="sxs-lookup"><span data-stu-id="ae1f7-119">-debug</span></span>|<span data-ttu-id="ae1f7-120">Bir uygulama etkinleştirilirken bırakmaz için işleme veya mağaza'dan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="ae1f7-121">Bu, yalnızca yerel bir dosyaya etkinleştirildiğinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="ae1f7-122">-debugSecurityZoneURL \<URL'si ></span><span class="sxs-lookup"><span data-stu-id="ae1f7-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="ae1f7-123">İle kullanılan bir [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] PresentationHost.exe için gibi dağıtıldıysa uygulamanın hata ayıklaması belirtmek için değer belirtilen [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae1f7-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="ae1f7-124">Bu dağıtım bölgesi hem kaynak siteyi belirler.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="ae1f7-125">-ekleme</span><span class="sxs-lookup"><span data-stu-id="ae1f7-125">-embedding</span></span>|<span data-ttu-id="ae1f7-126">OLE için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-126">Required by OLE.</span></span> <span data-ttu-id="ae1f7-127">Varsa `-event` veya `-debug` parametresi belirtilirse, belirtmek gerekli değil `-embedding` parametresi, çünkü bu parametre, dahili olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="ae1f7-128">-olay \<eventname ></span><span class="sxs-lookup"><span data-stu-id="ae1f7-128">-event \<eventname></span></span>|<span data-ttu-id="ae1f7-129">Bu ada sahip olayı açın ve PresentationHost.exe konak başlatıldı ve hazır olduğunda sinyal [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] içeriği.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="ae1f7-130">PresentationHost.exe sonlandırılacak olay açılırken bir hata olduğunda, IF gibi onu değil zaten oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="ae1f7-131">-launchApplication \<URL'si ></span><span class="sxs-lookup"><span data-stu-id="ae1f7-131">-launchApplication \<url></span></span>|<span data-ttu-id="ae1f7-132">Tek başına bir başlatır [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] belirtilen URL'den uygulama.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-132">Launches a standalone [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] application from the specified URL.</span></span> [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] <span data-ttu-id="ae1f7-133">ve .NET uygulamaları ile ilgili WinINet güvenlik ilkesi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-133">and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="ae1f7-134">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="ae1f7-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="ae1f7-135">Kabuk işleyicisi</span><span class="sxs-lookup"><span data-stu-id="ae1f7-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="ae1f7-136">MIME işleyicisi</span><span class="sxs-lookup"><span data-stu-id="ae1f7-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="ae1f7-137">Visual Studio hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ae1f7-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="ae1f7-138">Visual Studio bölgede hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ae1f7-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="ae1f7-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae1f7-139">See also</span></span>

- [<span data-ttu-id="ae1f7-140">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="ae1f7-140">Security</span></span>](../security-wpf.md)
