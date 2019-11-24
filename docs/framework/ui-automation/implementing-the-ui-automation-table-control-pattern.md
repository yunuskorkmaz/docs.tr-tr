---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 8e929f181255f6738261533fa3261187ebe3c6ff
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447097"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="2a7f5-102">UI Otomasyonu Tablo Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="2a7f5-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="2a7f5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2a7f5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2a7f5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2a7f5-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="2a7f5-106">Links to additional references are listed at the end of the overview.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="2a7f5-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="2a7f5-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="2a7f5-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="2a7f5-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="2a7f5-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="2a7f5-111">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="2a7f5-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="2a7f5-112">When implementing the Table control pattern, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="2a7f5-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="2a7f5-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="2a7f5-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="2a7f5-115">Column and row headers may include both a primary header as well as any supporting headers.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a7f5-116">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-116">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="2a7f5-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="2a7f5-118">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-118">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="2a7f5-119">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="2a7f5-119">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="2a7f5-120">Example of a Table with Complex Column Headers</span><span class="sxs-lookup"><span data-stu-id="2a7f5-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="2a7f5-121">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="2a7f5-121">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="2a7f5-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span><span class="sxs-lookup"><span data-stu-id="2a7f5-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="2a7f5-123">Required Members for ITableProvider</span><span class="sxs-lookup"><span data-stu-id="2a7f5-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="2a7f5-124">The following properties and methods are required for the ITableProvider interface.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="2a7f5-125">Required members</span><span class="sxs-lookup"><span data-stu-id="2a7f5-125">Required members</span></span>|<span data-ttu-id="2a7f5-126">Member type</span><span class="sxs-lookup"><span data-stu-id="2a7f5-126">Member type</span></span>|<span data-ttu-id="2a7f5-127">Notlar</span><span class="sxs-lookup"><span data-stu-id="2a7f5-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="2a7f5-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="2a7f5-128">Property</span></span>|<span data-ttu-id="2a7f5-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="2a7f5-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2a7f5-130">Method</span></span>|<span data-ttu-id="2a7f5-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="2a7f5-132">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2a7f5-132">Method</span></span>|<span data-ttu-id="2a7f5-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-133">None</span></span>|  
  
 <span data-ttu-id="2a7f5-134">This control pattern has no associated events.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="2a7f5-135">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="2a7f5-135">Exceptions</span></span>  
 <span data-ttu-id="2a7f5-136">This control pattern has no associated exceptions.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7f5-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a7f5-137">See also</span></span>

- [<span data-ttu-id="2a7f5-138">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2a7f5-138">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="2a7f5-139">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="2a7f5-139">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="2a7f5-140">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="2a7f5-140">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="2a7f5-141">UI Otomasyonu TableItem Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="2a7f5-141">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="2a7f5-142">UI Otomasyonu Grid Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="2a7f5-142">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="2a7f5-143">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2a7f5-143">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="2a7f5-144">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="2a7f5-144">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
