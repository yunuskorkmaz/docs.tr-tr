---
title: "UI Otomasyon ScrollItem Denetim Düzeni Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ef089e72c3b8dd089db5022ea1808cee98c27ecd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="8e14e-102">UI Otomasyon ScrollItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="8e14e-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="8e14e-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8e14e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8e14e-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8e14e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8e14e-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IScrollItemProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="8e14e-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="8e14e-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8e14e-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="8e14e-107"><xref:System.Windows.Automation.ScrollItemPattern> Denetim düzeni tek tek alt denetimler uygulamak kapsayıcıların desteklemek için kullanılan <xref:System.Windows.Automation.Provider.IScrollProvider>.</span><span class="sxs-lookup"><span data-stu-id="8e14e-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="8e14e-108">Bu denetim düzeni alt denetim ve alt denetim görüntülemek için kendi görünüm penceresinin içinde kapsayıcı şu anda görünür içeriğe (veya bölge) değiştirebilirsiniz emin olmak için kapsayıcısının arasında bir iletişim kanalı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="8e14e-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="8e14e-109">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8e14e-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8e14e-110">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="8e14e-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8e14e-111">Kaydırma öğesi denetim deseni uygularken, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="8e14e-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="8e14e-112">İçinde bir pencere veya tuvale denetimi bulunan öğeleri IScrollItemProvider arabirimi uygulamak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8e14e-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="8e14e-113">Alternatif olarak, ancak bunlar için geçerli bir konum kullanıma gerekir <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span><span class="sxs-lookup"><span data-stu-id="8e14e-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="8e14e-114">Bu kullanmak için UI otomasyon istemci uygulaması sağlayacak <xref:System.Windows.Automation.ScrollPattern> denetim düzeni yöntemlere alt öğesi görüntülemek için kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="8e14e-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="8e14e-115">Gerekli üyeleri IScrollItemProvider için</span><span class="sxs-lookup"><span data-stu-id="8e14e-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="8e14e-116">Aşağıdaki yöntem, IScrollProvider arabirimi uygulamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8e14e-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="8e14e-117">Gerekli üyeleri</span><span class="sxs-lookup"><span data-stu-id="8e14e-117">Required members</span></span>|<span data-ttu-id="8e14e-118">Üye türü</span><span class="sxs-lookup"><span data-stu-id="8e14e-118">Member type</span></span>|<span data-ttu-id="8e14e-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="8e14e-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="8e14e-120">-Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e14e-120">-   Method</span></span>|<span data-ttu-id="8e14e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="8e14e-121">None</span></span>|  
  
 <span data-ttu-id="8e14e-122">Bu denetim düzeni ilişkili özellikleri ya da olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="8e14e-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="8e14e-123">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="8e14e-123">Exceptions</span></span>  
 <span data-ttu-id="8e14e-124">Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e14e-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="8e14e-125">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="8e14e-125">Exception Type</span></span>|<span data-ttu-id="8e14e-126">Koşul</span><span class="sxs-lookup"><span data-stu-id="8e14e-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="8e14e-127">Bir öğe görünüme kaydırılan edilemez ise:</span><span class="sxs-lookup"><span data-stu-id="8e14e-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="8e14e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e14e-128">See Also</span></span>  
 [<span data-ttu-id="8e14e-129">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8e14e-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="8e14e-130">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="8e14e-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="8e14e-131">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="8e14e-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="8e14e-132">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8e14e-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="8e14e-133">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="8e14e-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
