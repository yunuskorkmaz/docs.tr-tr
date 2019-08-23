---
title: UI Otomasyon ScrollItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 4883184d75a21efbc08947008baddf31346d7951
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935752"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="11cd4-102">UI Otomasyon ScrollItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="11cd4-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="11cd4-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="11cd4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="11cd4-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="11cd4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="11cd4-105">Bu konuda özellikler, Yöntemler ve olaylar hakkında bilgiler <xref:System.Windows.Automation.Provider.IScrollItemProvider>de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="11cd4-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="11cd4-106">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="11cd4-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="11cd4-107">Denetim stili, uygulayan <xref:System.Windows.Automation.Provider.IScrollProvider>kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır. <xref:System.Windows.Automation.ScrollItemPattern></span><span class="sxs-lookup"><span data-stu-id="11cd4-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="11cd4-108">Bu denetim stili, kapsayıcının kendi görünüm içindeki görünür içeriği (veya bölgeyi) alt denetimi görüntüleyecek şekilde değiştirebildiğinden emin olmak için bir alt denetim ve kapsayıcısı arasında bir iletişim kanalı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="11cd4-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="11cd4-109">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="11cd4-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="11cd4-110">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="11cd4-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="11cd4-111">Kaydırma öğesi denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="11cd4-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="11cd4-112">Bir pencere veya tuval denetiminde bulunan öğelerin ıcrollitemprovider arabirimini uygulaması için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="11cd4-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="11cd4-113">Ancak alternatif olarak, için <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>geçerli bir konum kullanıma sunmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="11cd4-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="11cd4-114">Bu, bir UI Otomasyonu istemci uygulamasının alt öğeyi göstermek için <xref:System.Windows.Automation.ScrollPattern> kapsayıcıda denetim deseninin yöntemlerini kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="11cd4-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="11cd4-115">Icrollitemprovider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="11cd4-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="11cd4-116">IScrollProvider arabirimini uygulamak için aşağıdaki yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="11cd4-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="11cd4-117">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="11cd4-117">Required members</span></span>|<span data-ttu-id="11cd4-118">Üye türü</span><span class="sxs-lookup"><span data-stu-id="11cd4-118">Member type</span></span>|<span data-ttu-id="11cd4-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="11cd4-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="11cd4-120">-Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11cd4-120">-   Method</span></span>|<span data-ttu-id="11cd4-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="11cd4-121">None</span></span>|  
  
 <span data-ttu-id="11cd4-122">Bu denetim deseninin ilişkili özellikleri veya olayları yok.</span><span class="sxs-lookup"><span data-stu-id="11cd4-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="11cd4-123">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="11cd4-123">Exceptions</span></span>  
 <span data-ttu-id="11cd4-124">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="11cd4-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="11cd4-125">Özel Durum Türü</span><span class="sxs-lookup"><span data-stu-id="11cd4-125">Exception Type</span></span>|<span data-ttu-id="11cd4-126">Koşul</span><span class="sxs-lookup"><span data-stu-id="11cd4-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="11cd4-127">Bir öğe görünüme kaydırılayoksa:</span><span class="sxs-lookup"><span data-stu-id="11cd4-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="11cd4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11cd4-128">See also</span></span>

- [<span data-ttu-id="11cd4-129">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="11cd4-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="11cd4-130">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="11cd4-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="11cd4-131">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="11cd4-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="11cd4-132">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="11cd4-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="11cd4-133">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="11cd4-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
