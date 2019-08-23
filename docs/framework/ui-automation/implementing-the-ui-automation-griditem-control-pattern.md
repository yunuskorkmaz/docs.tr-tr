---
title: UI Otomasyon GridItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 1fa0de86ee59a48d0d64156b41ad2db794dff761
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968880"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="5ab0c-102">UI Otomasyon GridItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="5ab0c-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="5ab0c-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5ab0c-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5ab0c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5ab0c-105">Bu konu, özellikler hakkında bilgiler de dahil <xref:System.Windows.Automation.Provider.IGridItemProvider>olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="5ab0c-106">Ek başvuruların bağlantıları genel bakış sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="5ab0c-107">Denetim stili, uygulayan <xref:System.Windows.Automation.Provider.IGridProvider>kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır. <xref:System.Windows.Automation.GridItemPattern></span><span class="sxs-lookup"><span data-stu-id="5ab0c-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="5ab0c-108">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5ab0c-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5ab0c-109">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="5ab0c-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5ab0c-110">Uygulama <xref:System.Windows.Automation.Provider.IGridProvider>sırasında, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5ab0c-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="5ab0c-111">Izgara koordinatları, koordinatlara (0, 0) sahip üstteki sol hücreyle sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="5ab0c-112">Birleştirilmiş hücreler, Kullanıcı arabirimi <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> Otomasyonu <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> sağlayıcısı tarafından tanımlanan temel alınan bağlantı hücrelerine göre ve özelliklerini raporlar.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="5ab0c-113">Genellikle, en üstteki ve en soldaki satır veya sütun olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="5ab0c-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>, hücreleri birleştirme veya bölme gibi, kılavuzun etkin olarak düzenlenmesini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="5ab0c-115">Uygulayan <xref:System.Windows.Automation.Provider.IGridItemProvider> denetimler genellikle, klavyeyi kullanarak (bir UI Otomasyon istemcisi bitişik denetimlere taşınabilir) geçebilir.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="5ab0c-116">IGridItemProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="5ab0c-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="5ab0c-117">Uygulamak <xref:System.Windows.Automation.Provider.IGridItemProvider>için aşağıdaki özellikler ve Yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="5ab0c-118">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="5ab0c-118">Required members</span></span>|<span data-ttu-id="5ab0c-119">Üye türü</span><span class="sxs-lookup"><span data-stu-id="5ab0c-119">Member type</span></span>|<span data-ttu-id="5ab0c-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="5ab0c-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="5ab0c-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="5ab0c-121">Property</span></span>|<span data-ttu-id="5ab0c-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="5ab0c-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="5ab0c-123">Property</span></span>|<span data-ttu-id="5ab0c-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="5ab0c-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="5ab0c-125">Property</span></span>|<span data-ttu-id="5ab0c-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="5ab0c-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="5ab0c-127">Property</span></span>|<span data-ttu-id="5ab0c-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="5ab0c-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="5ab0c-129">Property</span></span>|<span data-ttu-id="5ab0c-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-130">None</span></span>|  
  
 <span data-ttu-id="5ab0c-131">Bu denetim deseninin ilişkili yöntemleri veya olayları yok.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5ab0c-132">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="5ab0c-132">Exceptions</span></span>  
 <span data-ttu-id="5ab0c-133">Bu denetim deseninin ilişkili özel durumları yok.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab0c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ab0c-134">See also</span></span>

- [<span data-ttu-id="5ab0c-135">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5ab0c-135">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5ab0c-136">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="5ab0c-136">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="5ab0c-137">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="5ab0c-137">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5ab0c-138">UI Otomasyonu Grid Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="5ab0c-138">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="5ab0c-139">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5ab0c-139">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="5ab0c-140">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="5ab0c-140">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
