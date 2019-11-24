---
title: UI Otomasyon MultipleView Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: c9199e0ea1971c22bfc1f6334b9d2d9d73bb048c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435060"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="77758-102">UI Otomasyon MultipleView Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="77758-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="77758-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="77758-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="77758-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="77758-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="77758-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span><span class="sxs-lookup"><span data-stu-id="77758-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="77758-106">Links to additional references are listed at the end of the topic.</span><span class="sxs-lookup"><span data-stu-id="77758-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="77758-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span><span class="sxs-lookup"><span data-stu-id="77758-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="77758-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span><span class="sxs-lookup"><span data-stu-id="77758-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="77758-109">The supported views are determined by the control developer and are specific to each control.</span><span class="sxs-lookup"><span data-stu-id="77758-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="77758-110">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="77758-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="77758-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="77758-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="77758-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span><span class="sxs-lookup"><span data-stu-id="77758-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="77758-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span><span class="sxs-lookup"><span data-stu-id="77758-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="77758-114">A control that is able to sort its content is not considered to support multiple views.</span><span class="sxs-lookup"><span data-stu-id="77758-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="77758-115">The collection of views must be identical across instances.</span><span class="sxs-lookup"><span data-stu-id="77758-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="77758-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span><span class="sxs-lookup"><span data-stu-id="77758-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="77758-117">Required Members for IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="77758-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="77758-118">The following properties and methods are required for implementing IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="77758-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="77758-119">Required members</span><span class="sxs-lookup"><span data-stu-id="77758-119">Required members</span></span>|<span data-ttu-id="77758-120">Member type</span><span class="sxs-lookup"><span data-stu-id="77758-120">Member type</span></span>|<span data-ttu-id="77758-121">Notlar</span><span class="sxs-lookup"><span data-stu-id="77758-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="77758-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="77758-122">Property</span></span>|<span data-ttu-id="77758-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="77758-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="77758-124">Yöntem</span><span class="sxs-lookup"><span data-stu-id="77758-124">Method</span></span>|<span data-ttu-id="77758-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="77758-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="77758-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="77758-126">Method</span></span>|<span data-ttu-id="77758-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="77758-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="77758-128">Yöntem</span><span class="sxs-lookup"><span data-stu-id="77758-128">Method</span></span>|<span data-ttu-id="77758-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="77758-129">None</span></span>|  
  
 <span data-ttu-id="77758-130">There are no events associated with this control pattern.</span><span class="sxs-lookup"><span data-stu-id="77758-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="77758-131">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="77758-131">Exceptions</span></span>  
 <span data-ttu-id="77758-132">Provider must throw the following exceptions.</span><span class="sxs-lookup"><span data-stu-id="77758-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="77758-133">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="77758-133">Exception type</span></span>|<span data-ttu-id="77758-134">Koşul</span><span class="sxs-lookup"><span data-stu-id="77758-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="77758-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span><span class="sxs-lookup"><span data-stu-id="77758-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77758-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77758-136">See also</span></span>

- [<span data-ttu-id="77758-137">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="77758-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="77758-138">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="77758-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="77758-139">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="77758-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="77758-140">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="77758-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="77758-141">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="77758-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
