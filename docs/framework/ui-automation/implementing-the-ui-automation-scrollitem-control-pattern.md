---
title: UI Otomasyon ScrollItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
ms.openlocfilehash: 3a0647ab98dcb86306573a0e9826fa7232fa9ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180137"
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="4252e-102">UI Otomasyon ScrollItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="4252e-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="4252e-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4252e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4252e-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="4252e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="4252e-105">Bu konu, özellikleri, yöntemleri ve <xref:System.Windows.Automation.Provider.IScrollItemProvider>olayları hakkında bilgi de dahil olmak üzere, uygulamak için kurallar ve sözleşmeler tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4252e-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="4252e-106">Ek başvurulara bağlantılar konunun sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="4252e-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="4252e-107">Denetim <xref:System.Windows.Automation.ScrollItemPattern> deseni, uygulayan <xref:System.Windows.Automation.Provider.IScrollProvider>kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4252e-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="4252e-108">Bu denetim deseni, kapsayıcının alt denetimi görüntülemek için görünüm portu içindeki şu anda görünen içeriği (veya bölgeyi) değiştirebilmesini sağlamak için alt denetim ve kapsayıcısı arasında bir iletişim kanalı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="4252e-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="4252e-109">Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4252e-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="4252e-110">Uygulama Yönergeleri ve Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="4252e-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="4252e-111">Kaydırma Öğesi denetim deseni uygulanırken, aşağıdaki yönergeleri ve kuralları not edin:</span><span class="sxs-lookup"><span data-stu-id="4252e-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="4252e-112">IScrollItemProvider arabirimini uygulamak için Pencere veya Tuval denetiminde bulunan öğeler gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4252e-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="4252e-113">Alternatif olarak, ancak, onlar için geçerli <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>bir konum ortaya gerekir.</span><span class="sxs-lookup"><span data-stu-id="4252e-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="4252e-114">Bu, bir Kullanıcı Aracı Otomasyon istemcisi uygulamasının alt öğeyi <xref:System.Windows.Automation.ScrollPattern> görüntülemek için kapsayıcıdaki denetim deseni yöntemlerini kullanmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4252e-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="4252e-115">IScrollItemProvider için Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="4252e-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="4252e-116">IScrollProvider arabirimini uygulamak için aşağıdaki yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4252e-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="4252e-117">Gerekli üyeler</span><span class="sxs-lookup"><span data-stu-id="4252e-117">Required members</span></span>|<span data-ttu-id="4252e-118">Üye tipi</span><span class="sxs-lookup"><span data-stu-id="4252e-118">Member type</span></span>|<span data-ttu-id="4252e-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="4252e-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="4252e-120">- Yöntem</span><span class="sxs-lookup"><span data-stu-id="4252e-120">-   Method</span></span>|<span data-ttu-id="4252e-121">None</span><span class="sxs-lookup"><span data-stu-id="4252e-121">None</span></span>|  
  
 <span data-ttu-id="4252e-122">Bu denetim deseni ilişkili özellikleri veya olayları vardır.</span><span class="sxs-lookup"><span data-stu-id="4252e-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="4252e-123">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="4252e-123">Exceptions</span></span>  
 <span data-ttu-id="4252e-124">Sağlayıcılar aşağıdaki özel durumları atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4252e-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="4252e-125">Özel Durum Türü</span><span class="sxs-lookup"><span data-stu-id="4252e-125">Exception Type</span></span>|<span data-ttu-id="4252e-126">Koşul</span><span class="sxs-lookup"><span data-stu-id="4252e-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="4252e-127">Bir öğe görünüme kaydırılamıyorsa:</span><span class="sxs-lookup"><span data-stu-id="4252e-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="4252e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4252e-128">See also</span></span>

- [<span data-ttu-id="4252e-129">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4252e-129">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="4252e-130">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="4252e-130">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="4252e-131">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="4252e-131">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="4252e-132">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4252e-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="4252e-133">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="4252e-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
