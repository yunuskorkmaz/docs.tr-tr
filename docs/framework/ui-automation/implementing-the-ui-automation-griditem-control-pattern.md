---
title: UI Otomasyon GridItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: d561587e6bb98ba857b27ba89b4c1a45ba964ffd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180197"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="13178-102">UI Otomasyon GridItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="13178-102">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="13178-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="13178-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="13178-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="13178-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="13178-105">Bu <xref:System.Windows.Automation.Provider.IGridItemProvider>konu, özellikler hakkında bilgi de dahil olmak üzere uygulama yönergeleri ve kuralları sunar.</span><span class="sxs-lookup"><span data-stu-id="13178-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="13178-106">Ek başvurulara bağlantılar genel bakışın sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="13178-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="13178-107">Denetim <xref:System.Windows.Automation.GridItemPattern> deseni, uygulayan <xref:System.Windows.Automation.Provider.IGridProvider>kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13178-107">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="13178-108">Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="13178-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="13178-109">Uygulama Yönergeleri ve Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="13178-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="13178-110">Uygularken <xref:System.Windows.Automation.Provider.IGridProvider>aşağıdaki yönergeleri ve kuralları unutmayın:</span><span class="sxs-lookup"><span data-stu-id="13178-110">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="13178-111">Izgara koordinatları, sol üst hücrenin koordinatları (0, 0) olan sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="13178-111">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="13178-112">Birleştirilmiş hücreler, <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> UI Automation sağlayıcısı tarafından tanımlandığı şekilde temel bağlantı hücrelerine göre kendi özelliklerini ve <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> özelliklerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="13178-112">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="13178-113">Genellikle, en üstteki ve en soldaki satır veya sütun olur.</span><span class="sxs-lookup"><span data-stu-id="13178-113">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="13178-114"><xref:System.Windows.Automation.Provider.IGridItemProvider>hücrelerin birleştirilmesi veya bölünmesi gibi ızgaranın etkin bir şekilde manipüle sini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="13178-114"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="13178-115">Uygulayan <xref:System.Windows.Automation.Provider.IGridItemProvider> denetimler genellikle klavyeyi kullanarak geçiş yapılabilir (diğer bir şekilde, bir UI Automation istemcisi bitişik denetimlere geçebilir).</span><span class="sxs-lookup"><span data-stu-id="13178-115">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="13178-116">IGridItemProvider için Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="13178-116">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="13178-117">Uygulamak için aşağıdaki özellikler ve <xref:System.Windows.Automation.Provider.IGridItemProvider>yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="13178-117">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="13178-118">Gerekli üyeler</span><span class="sxs-lookup"><span data-stu-id="13178-118">Required members</span></span>|<span data-ttu-id="13178-119">Üye tipi</span><span class="sxs-lookup"><span data-stu-id="13178-119">Member type</span></span>|<span data-ttu-id="13178-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="13178-120">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="13178-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="13178-121">Property</span></span>|<span data-ttu-id="13178-122">None</span><span class="sxs-lookup"><span data-stu-id="13178-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="13178-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="13178-123">Property</span></span>|<span data-ttu-id="13178-124">None</span><span class="sxs-lookup"><span data-stu-id="13178-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="13178-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="13178-125">Property</span></span>|<span data-ttu-id="13178-126">None</span><span class="sxs-lookup"><span data-stu-id="13178-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="13178-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="13178-127">Property</span></span>|<span data-ttu-id="13178-128">None</span><span class="sxs-lookup"><span data-stu-id="13178-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="13178-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="13178-129">Property</span></span>|<span data-ttu-id="13178-130">None</span><span class="sxs-lookup"><span data-stu-id="13178-130">None</span></span>|  
  
 <span data-ttu-id="13178-131">Bu denetim deseni ilişkili yöntem veya olay vardır.</span><span class="sxs-lookup"><span data-stu-id="13178-131">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="13178-132">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="13178-132">Exceptions</span></span>  
 <span data-ttu-id="13178-133">Bu denetim deseni ilişkili özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="13178-133">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13178-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13178-134">See also</span></span>

- [<span data-ttu-id="13178-135">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="13178-135">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="13178-136">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="13178-136">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="13178-137">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="13178-137">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="13178-138">UI Otomasyonu Grid Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="13178-138">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="13178-139">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="13178-139">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="13178-140">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="13178-140">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
