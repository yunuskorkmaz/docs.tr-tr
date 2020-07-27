---
title: UI Otomasyon GridItem Denetim Düzeni Uygulama
description: UI otomasyonunda kılavuz öğeleri için GridItemPattern denetim modelini uygulamaya yönelik kılavuzları ve kuralları öğrenin. IGridItemProvider için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: e0a0c616f3f0cf9bc091e4fbb496d71ab8550bd3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165828"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a><span data-ttu-id="b010b-104">UI Otomasyon GridItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="b010b-104">Implementing the UI Automation GridItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="b010b-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="b010b-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b010b-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="b010b-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="b010b-107">Bu konu <xref:System.Windows.Automation.Provider.IGridItemProvider> , özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="b010b-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>, including information about properties.</span></span> <span data-ttu-id="b010b-108">Ek başvuruların bağlantıları genel bakış sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="b010b-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="b010b-109"><xref:System.Windows.Automation.GridItemPattern>Denetim stili, uygulayan kapsayıcıların tek tek alt denetimlerini desteklemek için kullanılır <xref:System.Windows.Automation.Provider.IGridProvider> .</span><span class="sxs-lookup"><span data-stu-id="b010b-109">The <xref:System.Windows.Automation.GridItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span> <span data-ttu-id="b010b-110">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b010b-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b010b-111">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="b010b-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="b010b-112">Uygulama sırasında <xref:System.Windows.Automation.Provider.IGridProvider> , aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b010b-112">When implementing <xref:System.Windows.Automation.Provider.IGridProvider>, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="b010b-113">Izgara koordinatları, koordinatlara (0, 0) sahip üstteki sol hücreyle sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="b010b-113">Grid coordinates are zero-based with the upper left cell having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="b010b-114">Birleştirilmiş hücreler, <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> Kullanıcı Arabirimi Otomasyonu sağlayıcısı tarafından tanımlanan temel alınan bağlantı hücrelerine göre ve özelliklerini raporlar.</span><span class="sxs-lookup"><span data-stu-id="b010b-114">Merged cells will report their <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> and <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> properties based on their underlying anchor cell as defined by the UI Automation provider.</span></span> <span data-ttu-id="b010b-115">Genellikle, en üstteki ve en soldaki satır veya sütun olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b010b-115">Typically, it will be the topmost and leftmost row or column.</span></span>  
  
- <span data-ttu-id="b010b-116"><xref:System.Windows.Automation.Provider.IGridItemProvider>, hücreleri birleştirme veya bölme gibi, kılavuzun etkin olarak düzenlenmesini sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b010b-116"><xref:System.Windows.Automation.Provider.IGridItemProvider> does not provide for active manipulation of the grid such as merging or splitting cells.</span></span>  
  
- <span data-ttu-id="b010b-117">Uygulayan denetimler <xref:System.Windows.Automation.Provider.IGridItemProvider> genellikle, klavyeyi kullanarak (bır UI Otomasyon istemcisi bitişik denetimlere taşınabilir) geçebilir.</span><span class="sxs-lookup"><span data-stu-id="b010b-117">Controls that implement <xref:System.Windows.Automation.Provider.IGridItemProvider> can typically be traversed (that is, a UI Automation client can move to adjacent controls) by using the keyboard.</span></span>  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a><span data-ttu-id="b010b-118">IGridItemProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="b010b-118">Required Members for IGridItemProvider</span></span>  
 <span data-ttu-id="b010b-119">Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.IGridItemProvider> .</span><span class="sxs-lookup"><span data-stu-id="b010b-119">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span>  
  
|<span data-ttu-id="b010b-120">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="b010b-120">Required members</span></span>|<span data-ttu-id="b010b-121">Üye türü</span><span class="sxs-lookup"><span data-stu-id="b010b-121">Member type</span></span>|<span data-ttu-id="b010b-122">Notlar</span><span class="sxs-lookup"><span data-stu-id="b010b-122">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|<span data-ttu-id="b010b-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="b010b-123">Property</span></span>|<span data-ttu-id="b010b-124">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="b010b-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|<span data-ttu-id="b010b-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="b010b-125">Property</span></span>|<span data-ttu-id="b010b-126">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="b010b-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|<span data-ttu-id="b010b-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="b010b-127">Property</span></span>|<span data-ttu-id="b010b-128">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="b010b-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|<span data-ttu-id="b010b-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="b010b-129">Property</span></span>|<span data-ttu-id="b010b-130">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="b010b-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|<span data-ttu-id="b010b-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="b010b-131">Property</span></span>|<span data-ttu-id="b010b-132">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="b010b-132">None</span></span>|  
  
 <span data-ttu-id="b010b-133">Bu denetim deseninin ilişkili yöntemleri veya olayları yok.</span><span class="sxs-lookup"><span data-stu-id="b010b-133">This control pattern has no associated methods or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="b010b-134">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="b010b-134">Exceptions</span></span>  
 <span data-ttu-id="b010b-135">Bu denetim deseninin ilişkili özel durumları yok.</span><span class="sxs-lookup"><span data-stu-id="b010b-135">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b010b-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b010b-136">See also</span></span>

- [<span data-ttu-id="b010b-137">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b010b-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="b010b-138">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="b010b-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="b010b-139">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="b010b-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="b010b-140">UI Otomasyon Kılavuz Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="b010b-140">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="b010b-141">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b010b-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="b010b-142">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="b010b-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
