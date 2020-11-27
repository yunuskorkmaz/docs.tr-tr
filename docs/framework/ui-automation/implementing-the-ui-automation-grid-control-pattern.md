---
title: UI Otomasyon Kılavuz Denetim Düzenini Uygulama
description: UI otomasyonunda Griddeseninin kılavuz denetim deseninin uygulanması için kılavuzları ve kuralları anlayın. Igrprovider arabirimini uygulamayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 2290fd91c8eee0ab969eef2827d3c7440ef21e20
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274887"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="75dff-104">UI Otomasyon Kılavuz Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="75dff-104">Implementing the UI Automation Grid Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="75dff-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="75dff-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="75dff-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="75dff-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="75dff-107">Bu konuda <xref:System.Windows.Automation.Provider.IGridProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75dff-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="75dff-108">Ek başvuruların bağlantıları genel bakış sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="75dff-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="75dff-109"><xref:System.Windows.Automation.GridPattern>Denetim stili, alt öğelerin bir koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75dff-109">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="75dff-110">Bu öğenin alt öğeleri, <xref:System.Windows.Automation.Provider.IGridItemProvider> satır ve sütun tarafından geçilen iki boyutlu bir mantıksal koordinat sisteminde uygulamanız ve düzenlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="75dff-110">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="75dff-111">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="75dff-111">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="75dff-112">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="75dff-112">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="75dff-113">Kılavuz denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="75dff-113">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="75dff-114">Izgara koordinatları, koordinatlara sahip (0, 0) sol üst (veya yerel ayara bağlı olarak sağ üst hücre) ile sıfır tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="75dff-114">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="75dff-115">Bir hücre boşsa, bu hücrenin özelliğini desteklemek için bir UI Otomasyon öğesi döndürülmeye devam etmelidir <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> .</span><span class="sxs-lookup"><span data-stu-id="75dff-115">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="75dff-116">Kılavuzdaki alt öğelerin düzeni düzensiz bir diziye benzediğinde bu mümkündür (aşağıdaki örneğe bakın).</span><span class="sxs-lookup"><span data-stu-id="75dff-116">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="75dff-117">![Düzensiz düzeni gösteren Windows Gezgini görünümü.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="75dff-117">![Windows Explorer view showing ragged layout.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="75dff-118">Boş koordinatları olan Grid denetimine örnek</span><span class="sxs-lookup"><span data-stu-id="75dff-118">Example of a Grid Control with Empty Coordinates</span></span>  
  
- <span data-ttu-id="75dff-119">Tek bir öğe içeren bir ızgara, <xref:System.Windows.Automation.Provider.IGridProvider> mantıksal olarak bir kılavuz olarak kabul edildiğinde uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="75dff-119">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="75dff-120">Kılavuzdaki alt öğe öğelerinin sayısı immalzemedir.</span><span class="sxs-lookup"><span data-stu-id="75dff-120">The number of child items in the grid is immaterial.</span></span>  
  
- <span data-ttu-id="75dff-121">Sağlayıcı uygulamasına bağlı olarak gizli satırlar ve sütunlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaca yüklenebilir ve bu nedenle, <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> ve özelliklerine yansıtılacaktır <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> .</span><span class="sxs-lookup"><span data-stu-id="75dff-121">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="75dff-122">Gizli satırlar ve sütunlar henüz yüklenmediyse, bunlar sayılmaz.</span><span class="sxs-lookup"><span data-stu-id="75dff-122">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
- <span data-ttu-id="75dff-123"><xref:System.Windows.Automation.Provider.IGridProvider> bir kılavuzun etkin işlemesini etkinleştirmez; <xref:System.Windows.Automation.Provider.ITransformProvider> Bu işlevi etkinleştirmek için uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="75dff-123"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
- <span data-ttu-id="75dff-124"><xref:System.Windows.Automation.StructureChangedEventHandler>Eklenmiş, kaldırılmış veya birleştirilmiş hücreler gibi kılavuzda yapısal veya Düzen değişikliklerini dinlemek için bir kullanın.</span><span class="sxs-lookup"><span data-stu-id="75dff-124">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
- <span data-ttu-id="75dff-125">Bir <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> kılavuzun öğeleri veya hücreleri aracılığıyla çapraz geçişi izlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="75dff-125">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>

## <a name="required-members-for-igridprovider"></a><span data-ttu-id="75dff-126">Igrprovider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="75dff-126">Required Members for IGridProvider</span></span>  

 <span data-ttu-id="75dff-127">Aşağıdaki özellikler ve Yöntemler ıgrprovider arabirimini uygulamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="75dff-127">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="75dff-128">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="75dff-128">Required members</span></span>|<span data-ttu-id="75dff-129">Tür</span><span class="sxs-lookup"><span data-stu-id="75dff-129">Type</span></span>|<span data-ttu-id="75dff-130">Notlar</span><span class="sxs-lookup"><span data-stu-id="75dff-130">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="75dff-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="75dff-131">Property</span></span>|<span data-ttu-id="75dff-132">Yok</span><span class="sxs-lookup"><span data-stu-id="75dff-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="75dff-133">Özellik</span><span class="sxs-lookup"><span data-stu-id="75dff-133">Property</span></span>|<span data-ttu-id="75dff-134">Yok</span><span class="sxs-lookup"><span data-stu-id="75dff-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="75dff-135">Yöntem</span><span class="sxs-lookup"><span data-stu-id="75dff-135">Method</span></span>|<span data-ttu-id="75dff-136">Yok</span><span class="sxs-lookup"><span data-stu-id="75dff-136">None</span></span>|  
  
 <span data-ttu-id="75dff-137">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="75dff-137">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="75dff-138">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="75dff-138">Exceptions</span></span>  

 <span data-ttu-id="75dff-139">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="75dff-139">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="75dff-140">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="75dff-140">Exception type</span></span>|<span data-ttu-id="75dff-141">Koşul</span><span class="sxs-lookup"><span data-stu-id="75dff-141">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="75dff-142">-İstenen satır koordinatı öğesinden daha büyükse <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> veya sütun koordinatı öğesinden daha büyükse <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A> .</span><span class="sxs-lookup"><span data-stu-id="75dff-142">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="75dff-143">-İstenen satır veya sütun koordinatlarından herhangi biri sıfırdan küçükse.</span><span class="sxs-lookup"><span data-stu-id="75dff-143">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75dff-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75dff-144">See also</span></span>

- [<span data-ttu-id="75dff-145">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="75dff-145">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="75dff-146">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="75dff-146">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="75dff-147">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="75dff-147">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="75dff-148">UI Otomasyon GridItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="75dff-148">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="75dff-149">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="75dff-149">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="75dff-150">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="75dff-150">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
