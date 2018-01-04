---
title: "UI Otomasyon Kılavuz Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
caps.latest.revision: "27"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4667cd149940310e2422686b9e9fdf6e7e99ca9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="d4610-102">UI Otomasyon Kılavuz Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="d4610-102">Implementing the UI Automation Grid Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="d4610-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d4610-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d4610-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="d4610-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d4610-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IGridProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="d4610-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="d4610-106">Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d4610-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="d4610-107"><xref:System.Windows.Automation.GridPattern> Denetim düzeni alt öğe koleksiyonunu için kapsayıcı olarak hareket denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d4610-107">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="d4610-108">Bu öğenin alt öğeleri uygulamalıdır <xref:System.Windows.Automation.Provider.IGridItemProvider> ve satır ve sütun tarafından geçiş bir iki boyutlu mantıksal koordinat sistemi düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="d4610-108">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="d4610-109">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d4610-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d4610-110">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="d4610-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="d4610-111">Kılavuz denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="d4610-111">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="d4610-112">Kılavuz koordinatları, sol üst (veya üst sağ hücre yerel ayara bağlı olarak) koordinatları (0, 0) sahip sıfır tabanlı.</span><span class="sxs-lookup"><span data-stu-id="d4610-112">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
-   <span data-ttu-id="d4610-113">Bir hücre boşsa, UI Otomasyon öğesi hala desteklemek için döndürülmelidir <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> hücre için özellik.</span><span class="sxs-lookup"><span data-stu-id="d4610-113">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="d4610-114">Alt öğeler kılavuzunda düzenini düzensiz bir diziye benzer olduğunda bu mümkündür (aşağıdaki örneğe bakın).</span><span class="sxs-lookup"><span data-stu-id="d4610-114">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="d4610-115">![Windows Gezgini Dağınık düzeni gösteren görüntüleyin. ] (../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="d4610-115">![Windows Explorer view showing ragged layout.](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="d4610-116">Kılavuz Denetim boş koordinatları ile örneği</span><span class="sxs-lookup"><span data-stu-id="d4610-116">Example of a Grid Control with Empty Coordinates</span></span>  
  
-   <span data-ttu-id="d4610-117">Tek bir öğe içeren bir kılavuz uygulamak için hala gereklidir <xref:System.Windows.Automation.Provider.IGridProvider> , mantıksal bir kılavuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d4610-117">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="d4610-118">Alt öğeler kılavuzunda kurucularýn sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="d4610-118">The number of child items in the grid is immaterial.</span></span>  
  
-   <span data-ttu-id="d4610-119">Gizli satırları ve sütunları sağlayıcıyı uygulama bağlı yüklenmesi de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı ve bu nedenle yansıtılır <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> ve <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="d4610-119">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="d4610-120">Gizli satırları ve sütunları henüz yüklenmedi, bunlar alınmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="d4610-120">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
-   <span data-ttu-id="d4610-121"><xref:System.Windows.Automation.Provider.IGridProvider>etkin bir kılavuz işlenmesini etkinleştirmez; <xref:System.Windows.Automation.Provider.ITransformProvider> bu işlevselliği etkinleştirmek için uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4610-121"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
-   <span data-ttu-id="d4610-122">Kullanım bir <xref:System.Windows.Automation.StructureChangedEventHandler> kılavuz eklenmiş, kaldırılmış, birleştirilmiş veya hücreleri gibi yapısal veya düzen değişiklikleri dinlemek için.</span><span class="sxs-lookup"><span data-stu-id="d4610-122">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
-   <span data-ttu-id="d4610-123">Kullanım bir <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> öğeler veya kılavuz hücrelerini aracılığıyla geçişi izlemek için.</span><span class="sxs-lookup"><span data-stu-id="d4610-123">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a><span data-ttu-id="d4610-124">Gerekli üyeleri IGridProvider için</span><span class="sxs-lookup"><span data-stu-id="d4610-124">Required Members for IGridProvider</span></span>  
 <span data-ttu-id="d4610-125">Aşağıdaki özellikleri ve yöntemleri IGridProvider arabirimi uygulamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d4610-125">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="d4610-126">Gerekli üyeleri</span><span class="sxs-lookup"><span data-stu-id="d4610-126">Required members</span></span>|<span data-ttu-id="d4610-127">Tür</span><span class="sxs-lookup"><span data-stu-id="d4610-127">Type</span></span>|<span data-ttu-id="d4610-128">Notlar</span><span class="sxs-lookup"><span data-stu-id="d4610-128">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="d4610-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="d4610-129">Property</span></span>|<span data-ttu-id="d4610-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4610-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="d4610-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="d4610-131">Property</span></span>|<span data-ttu-id="d4610-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4610-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="d4610-133">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d4610-133">Method</span></span>|<span data-ttu-id="d4610-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4610-134">None</span></span>|  
  
 <span data-ttu-id="d4610-135">Bu denetim düzeni ilişkili olay vardır.</span><span class="sxs-lookup"><span data-stu-id="d4610-135">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="d4610-136">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d4610-136">Exceptions</span></span>  
 <span data-ttu-id="d4610-137">Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4610-137">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="d4610-138">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="d4610-138">Exception type</span></span>|<span data-ttu-id="d4610-139">Koşul</span><span class="sxs-lookup"><span data-stu-id="d4610-139">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="d4610-140">-İstenen satır koordinat büyükse <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> veya sütun koordinat büyük <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span><span class="sxs-lookup"><span data-stu-id="d4610-140">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="d4610-141">-İstenen satır veya sütun koordinatları küçükse sıfır.</span><span class="sxs-lookup"><span data-stu-id="d4610-141">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4610-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4610-142">See Also</span></span>  
 [<span data-ttu-id="d4610-143">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4610-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="d4610-144">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="d4610-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="d4610-145">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="d4610-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="d4610-146">UI Otomasyonu GridItem Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="d4610-146">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="d4610-147">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4610-147">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="d4610-148">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="d4610-148">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
