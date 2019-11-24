---
title: UI Otomasyon TableItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 4374666ba5e03720413614c63b00ba987f81f58f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447088"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="41750-102">UI Otomasyon TableItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="41750-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="41750-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="41750-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="41750-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="41750-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="41750-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span><span class="sxs-lookup"><span data-stu-id="41750-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="41750-106">Links to additional references are listed at the end of the overview.</span><span class="sxs-lookup"><span data-stu-id="41750-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="41750-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="41750-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="41750-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="41750-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="41750-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span><span class="sxs-lookup"><span data-stu-id="41750-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="41750-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="41750-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="41750-111">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="41750-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="41750-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="41750-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="41750-113">Required Members for ITableItemProvider</span><span class="sxs-lookup"><span data-stu-id="41750-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="41750-114">Required member</span><span class="sxs-lookup"><span data-stu-id="41750-114">Required member</span></span>|<span data-ttu-id="41750-115">Member type</span><span class="sxs-lookup"><span data-stu-id="41750-115">Member type</span></span>|<span data-ttu-id="41750-116">Notlar</span><span class="sxs-lookup"><span data-stu-id="41750-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="41750-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="41750-117">Method</span></span>|<span data-ttu-id="41750-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="41750-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="41750-119">Yöntem</span><span class="sxs-lookup"><span data-stu-id="41750-119">Method</span></span>|<span data-ttu-id="41750-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="41750-120">None</span></span>|  
  
 <span data-ttu-id="41750-121">This control pattern has no associated properties or events.</span><span class="sxs-lookup"><span data-stu-id="41750-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="41750-122">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="41750-122">Exceptions</span></span>  
 <span data-ttu-id="41750-123">This control pattern has no associated exceptions.</span><span class="sxs-lookup"><span data-stu-id="41750-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41750-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41750-124">See also</span></span>

- [<span data-ttu-id="41750-125">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="41750-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="41750-126">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="41750-126">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="41750-127">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="41750-127">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="41750-128">UI Otomasyonu Table Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="41750-128">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="41750-129">UI Otomasyonu GridItem Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="41750-129">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="41750-130">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="41750-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="41750-131">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="41750-131">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
