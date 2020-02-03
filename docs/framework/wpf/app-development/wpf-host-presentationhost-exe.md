---
title: WPF Konağı (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743404"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="fe998-102">WPF Konağı (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="fe998-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="fe998-103">Windows Presentation Foundation (WPF) ana bilgisayarı (PresentationHost. exe), WPF uygulamalarının uyumlu tarayıcılarda barındırılmasına olanak tanıyan uygulamadır (Microsoft Internet Explorer 6 ve üzeri dahil).</span><span class="sxs-lookup"><span data-stu-id="fe998-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables WPF applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="fe998-104">Varsayılan olarak, Windows Presentation Foundation (WPF) ana bilgisayarı, tarayıcı tarafından barındırılan WPF içeriği için kabuk ve MIME işleyicisi olarak kaydedilir ve şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="fe998-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted WPF content, which includes:</span></span>  
  
- <span data-ttu-id="fe998-105">Gevşek (derlenmemiş) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyaları (. xaml).</span><span class="sxs-lookup"><span data-stu-id="fe998-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="fe998-106">XAML tarayıcısı uygulaması (XBAP) (. XBAP).</span><span class="sxs-lookup"><span data-stu-id="fe998-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="fe998-107">Bu türlerin dosyaları için Windows Presentation Foundation (WPF) ana bilgisayarı:</span><span class="sxs-lookup"><span data-stu-id="fe998-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="fe998-108">Windows Presentation Foundation (WPF) içeriğini barındırmak için kayıtlı HTML işleyicisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="fe998-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="fe998-109">Gerekli ortak dil çalışma zamanı (CLR) ve Windows Presentation Foundation (WPF) derlemelerinin doğru sürümlerini yükler.</span><span class="sxs-lookup"><span data-stu-id="fe998-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="fe998-110">Dağıtım bölgesi için uygun izin düzeylerinin yerinde olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe998-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="fe998-111">Bu konu, PresentationHost. exe ile kullanılabilecek komut satırı parametrelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe998-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="fe998-112">Kullanım</span><span class="sxs-lookup"><span data-stu-id="fe998-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="fe998-113">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe998-113">Parameters</span></span>  
  
|<span data-ttu-id="fe998-114">Parametre</span><span class="sxs-lookup"><span data-stu-id="fe998-114">Parameter</span></span>|<span data-ttu-id="fe998-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe998-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe998-116">filename</span><span class="sxs-lookup"><span data-stu-id="fe998-116">filename</span></span>|<span data-ttu-id="fe998-117">Etkinleştirilecek dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="fe998-117">The path of the file to be activated.</span></span> <span data-ttu-id="fe998-118">Ayrıca bir URI olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe998-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="fe998-119">-debug</span><span class="sxs-lookup"><span data-stu-id="fe998-119">-debug</span></span>|<span data-ttu-id="fe998-120">Bir uygulamayı etkinleştirirken, bir uygulamayı üzerinde yürütmez veya mağazadan çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="fe998-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="fe998-121">Bu yalnızca yerel bir dosya etkinleştirildiğinde işe yarar.</span><span class="sxs-lookup"><span data-stu-id="fe998-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="fe998-122">-debugSecurityZoneURL \<URL ></span><span class="sxs-lookup"><span data-stu-id="fe998-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="fe998-123">Bir uygulamanın, belirtilen URL 'den dağıtılarak hata ayıklaması gerektiğini PresentationHost. exe ' ye işaret eden bir URL değeriyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe998-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="fe998-124">Bu hem dağıtım bölgesini hem de kaynak sitesini belirler.</span><span class="sxs-lookup"><span data-stu-id="fe998-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="fe998-125">-Gömme</span><span class="sxs-lookup"><span data-stu-id="fe998-125">-embedding</span></span>|<span data-ttu-id="fe998-126">OLE tarafından gerektirilir.</span><span class="sxs-lookup"><span data-stu-id="fe998-126">Required by OLE.</span></span> <span data-ttu-id="fe998-127">`-event` veya `-debug` parametresi belirtilirse, bu parametre dahili olarak ayarlandığı için `-embedding` parametresinin belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fe998-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="fe998-128">-Event \<EventName ></span><span class="sxs-lookup"><span data-stu-id="fe998-128">-event \<eventname></span></span>|<span data-ttu-id="fe998-129">Bu adı taşıyan olayı açın ve PresentationHost. exe başlatıldığında ve WPF içeriğini barındırmak için hazırsanız bunu işaret edin.</span><span class="sxs-lookup"><span data-stu-id="fe998-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host WPF content.</span></span> <span data-ttu-id="fe998-130">Olay açılırken bir hata oluşursa (örneğin, zaten oluşturulmadıysa) PresentationHost. exe sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fe998-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="fe998-131">-launchApplication \<URL ></span><span class="sxs-lookup"><span data-stu-id="fe998-131">-launchApplication \<url></span></span>|<span data-ttu-id="fe998-132">Belirtilen URL 'den tek başına ClickOnce uygulaması başlatır.</span><span class="sxs-lookup"><span data-stu-id="fe998-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="fe998-133">.NET uygulamaları ile ilgili Internet Explorer ve WinINet güvenlik ilkesi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe998-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="fe998-134">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="fe998-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="fe998-135">Kabuk Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="fe998-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="fe998-136">MIME Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="fe998-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="fe998-137">Visual Studio hata ayıklaması</span><span class="sxs-lookup"><span data-stu-id="fe998-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="fe998-138">Bölgede Visual Studio hata ayıklaması</span><span class="sxs-lookup"><span data-stu-id="fe998-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="fe998-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe998-139">See also</span></span>

- [<span data-ttu-id="fe998-140">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="fe998-140">Security</span></span>](../security-wpf.md)
