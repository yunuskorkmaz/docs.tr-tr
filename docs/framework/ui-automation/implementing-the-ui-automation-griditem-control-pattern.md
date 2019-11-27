---
title: UI Otomasyon GridItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 832a53e072afc5533f2eeb7feb0cc326771cf23d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435260"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="9dd64-102">UI Otomasyon GridItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="9dd64-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="9dd64-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9dd64-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9dd64-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="9dd64-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9dd64-105">Bu konu, özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IGridItemProvider>uygulamak için kılavuz ve kuralları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="9dd64-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="9dd64-106">Ek başvuruların bağlantıları genel bakış sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="9dd64-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="9dd64-107"><xref:System.Windows.Automation.GridItemPattern> denetim stili, <xref:System.Windows.Automation.Provider.IGridProvider>uygulayan kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9dd64-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="9dd64-108">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9dd64-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9dd64-109">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="9dd64-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="9dd64-110"><xref:System.Windows.Automation.Provider.IGridProvider>uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9dd64-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="9dd64-111">Izgara koordinatları, koordinatlara (0, 0) sahip üstteki sol hücreyle sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="9dd64-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="9dd64-112">Birleştirilmiş hücreler, <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> ve <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> özelliklerini, Kullanıcı Arabirimi Otomasyonu sağlayıcısı tarafından tanımlanan temel alınan bağlayıcı hücrelerine göre rapor eder.</span><span class="sxs-lookup"><span data-stu-id="9dd64-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="9dd64-113">Genellikle, en üstteki ve en soldaki satır veya sütun olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9dd64-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="9dd64-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>, kılavuz için hücre birleştirme veya bölme gibi etkin düzenleme için sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="9dd64-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="9dd64-115"><xref:System.Windows.Automation.Provider.IGridItemProvider> uygulayan denetimler genellikle, klavyeyi kullanarak (bir UI Otomasyon istemcisi bitişik denetimlere taşınabilir) geçebilir.</span><span class="sxs-lookup"><span data-stu-id="9dd64-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="9dd64-116">IGridItemProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="9dd64-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="9dd64-117"><xref:System.Windows.Automation.Provider.IGridItemProvider>uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9dd64-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="9dd64-118">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="9dd64-118">Required members</span></span>|<span data-ttu-id="9dd64-119">Üye türü</span><span class="sxs-lookup"><span data-stu-id="9dd64-119">Member type</span></span>|<span data-ttu-id="9dd64-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="9dd64-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="9dd64-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="9dd64-121">Property</span></span>|<span data-ttu-id="9dd64-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="9dd64-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="9dd64-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="9dd64-123">Property</span></span>|<span data-ttu-id="9dd64-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="9dd64-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="9dd64-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="9dd64-125">Property</span></span>|<span data-ttu-id="9dd64-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="9dd64-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="9dd64-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="9dd64-127">Property</span></span>|<span data-ttu-id="9dd64-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="9dd64-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="9dd64-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="9dd64-129">Property</span></span>|<span data-ttu-id="9dd64-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="9dd64-130">None</span></span>|  
  
 <span data-ttu-id="9dd64-131">Bu denetim deseninin ilişkili yöntemleri veya olayları yok.</span><span class="sxs-lookup"><span data-stu-id="9dd64-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="9dd64-132">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="9dd64-132">Exceptions</span></span>  
 <span data-ttu-id="9dd64-133">Bu denetim deseninin ilişkili özel durumları yok.</span><span class="sxs-lookup"><span data-stu-id="9dd64-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd64-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd64-134">See also</span></span>

- [<span data-ttu-id="9dd64-135">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9dd64-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9dd64-136">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="9dd64-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9dd64-137">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="9dd64-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9dd64-138">UI Otomasyonu Grid Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="9dd64-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="9dd64-139">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9dd64-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="9dd64-140">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="9dd64-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
