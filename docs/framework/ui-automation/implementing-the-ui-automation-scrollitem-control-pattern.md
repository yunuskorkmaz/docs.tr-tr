---
title: UI Otomasyon ScrollItem Denetim Düzeni Uygulama
description: UI otomasyonunda Scrollıdıtem denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. Icrollitemprovider arabirimi için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 3274f75af0ca055547a75fd8db6384ddb0f59483
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239243"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="716b9-104">UI Otomasyon ScrollItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="716b9-104">Implementing the UI Automation ScrollItem Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="716b9-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="716b9-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="716b9-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="716b9-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="716b9-107">Bu konuda <xref:System.Windows.Automation.Provider.IScrollItemProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="716b9-107">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="716b9-108">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="716b9-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="716b9-109"><xref:System.Windows.Automation.ScrollItemPattern>Denetim stili, uygulayan kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır <xref:System.Windows.Automation.Provider.IScrollProvider> .</span><span class="sxs-lookup"><span data-stu-id="716b9-109">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="716b9-110">Bu denetim stili, kapsayıcının kendi görünüm içindeki görünür içeriği (veya bölgeyi) alt denetimi görüntüleyecek şekilde değiştirebildiğinden emin olmak için bir alt denetim ve kapsayıcısı arasında bir iletişim kanalı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="716b9-110">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="716b9-111">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="716b9-111">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="716b9-112">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="716b9-112">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="716b9-113">Kaydırma öğesi denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="716b9-113">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="716b9-114">Bir pencere veya tuval denetiminde bulunan öğelerin ıcrollitemprovider arabirimini uygulaması için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="716b9-114">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="716b9-115">Ancak alternatif olarak, için geçerli bir konum kullanıma sunmaları gerekir <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .</span><span class="sxs-lookup"><span data-stu-id="716b9-115">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="716b9-116">Bu, bir UI Otomasyonu istemci uygulamasının <xref:System.Windows.Automation.ScrollPattern> alt öğeyi göstermek için kapsayıcıda denetim deseninin yöntemlerini kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="716b9-116">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>

## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="716b9-117">Icrollitemprovider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="716b9-117">Required Members for IScrollItemProvider</span></span>  

 <span data-ttu-id="716b9-118">IScrollProvider arabirimini uygulamak için aşağıdaki yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="716b9-118">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="716b9-119">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="716b9-119">Required members</span></span>|<span data-ttu-id="716b9-120">Üye türü</span><span class="sxs-lookup"><span data-stu-id="716b9-120">Member type</span></span>|<span data-ttu-id="716b9-121">Notlar</span><span class="sxs-lookup"><span data-stu-id="716b9-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="716b9-122">-Yöntemi</span><span class="sxs-lookup"><span data-stu-id="716b9-122">-   Method</span></span>|<span data-ttu-id="716b9-123">Yok</span><span class="sxs-lookup"><span data-stu-id="716b9-123">None</span></span>|  
  
 <span data-ttu-id="716b9-124">Bu denetim deseninin ilişkili özellikleri veya olayları yok.</span><span class="sxs-lookup"><span data-stu-id="716b9-124">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="716b9-125">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="716b9-125">Exceptions</span></span>  

 <span data-ttu-id="716b9-126">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="716b9-126">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="716b9-127">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="716b9-127">Exception Type</span></span>|<span data-ttu-id="716b9-128">Koşul</span><span class="sxs-lookup"><span data-stu-id="716b9-128">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="716b9-129">Bir öğe görünüme kaydırılayoksa:</span><span class="sxs-lookup"><span data-stu-id="716b9-129">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="716b9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="716b9-130">See also</span></span>

- [<span data-ttu-id="716b9-131">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="716b9-131">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="716b9-132">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="716b9-132">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="716b9-133">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="716b9-133">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="716b9-134">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="716b9-134">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="716b9-135">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="716b9-135">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
