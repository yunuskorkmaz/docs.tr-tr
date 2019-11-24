---
title: UI Otomasyonu Pencere Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: d8afaa13bd4eca9f9fcd4c8ed26c09c62ad74931
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447036"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="e0572-102">UI Otomasyonu Pencere Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="e0572-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="e0572-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="e0572-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e0572-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e0572-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e0572-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span><span class="sxs-lookup"><span data-stu-id="e0572-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="e0572-106">Links to additional references are listed at the end of the topic.</span><span class="sxs-lookup"><span data-stu-id="e0572-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="e0572-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span><span class="sxs-lookup"><span data-stu-id="e0572-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="e0572-108">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span><span class="sxs-lookup"><span data-stu-id="e0572-108">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="e0572-109">Implementation Guidelines and Conventions</span><span class="sxs-lookup"><span data-stu-id="e0572-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="e0572-110">When implementing the Window control pattern, note the following guidelines and conventions:</span><span class="sxs-lookup"><span data-stu-id="e0572-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="e0572-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="e0572-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="e0572-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="e0572-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="e0572-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="e0572-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="e0572-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span><span class="sxs-lookup"><span data-stu-id="e0572-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="e0572-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span><span class="sxs-lookup"><span data-stu-id="e0572-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="e0572-116">Required Members for IWindowProvider</span><span class="sxs-lookup"><span data-stu-id="e0572-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="e0572-117">The following properties, methods, and events are required for the IWindowProvider interface.</span><span class="sxs-lookup"><span data-stu-id="e0572-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="e0572-118">Required member</span><span class="sxs-lookup"><span data-stu-id="e0572-118">Required member</span></span>|<span data-ttu-id="e0572-119">Member type</span><span class="sxs-lookup"><span data-stu-id="e0572-119">Member type</span></span>|<span data-ttu-id="e0572-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="e0572-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="e0572-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="e0572-121">Property</span></span>|<span data-ttu-id="e0572-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="e0572-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="e0572-123">Property</span></span>|<span data-ttu-id="e0572-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="e0572-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="e0572-125">Property</span></span>|<span data-ttu-id="e0572-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="e0572-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="e0572-127">Property</span></span>|<span data-ttu-id="e0572-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="e0572-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="e0572-129">Property</span></span>|<span data-ttu-id="e0572-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="e0572-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="e0572-131">Property</span></span>|<span data-ttu-id="e0572-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="e0572-133">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e0572-133">Method</span></span>|<span data-ttu-id="e0572-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="e0572-135">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e0572-135">Method</span></span>|<span data-ttu-id="e0572-136">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="e0572-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e0572-137">Method</span></span>|<span data-ttu-id="e0572-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="e0572-139">Olay</span><span class="sxs-lookup"><span data-stu-id="e0572-139">Event</span></span>|<span data-ttu-id="e0572-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="e0572-141">Olay</span><span class="sxs-lookup"><span data-stu-id="e0572-141">Event</span></span>|<span data-ttu-id="e0572-142">Yok.</span><span class="sxs-lookup"><span data-stu-id="e0572-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="e0572-143">Olay</span><span class="sxs-lookup"><span data-stu-id="e0572-143">Event</span></span>|<span data-ttu-id="e0572-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="e0572-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="e0572-145">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="e0572-145">Exceptions</span></span>  
 <span data-ttu-id="e0572-146">Providers must throw the following exceptions.</span><span class="sxs-lookup"><span data-stu-id="e0572-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="e0572-147">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="e0572-147">Exception type</span></span>|<span data-ttu-id="e0572-148">Koşul</span><span class="sxs-lookup"><span data-stu-id="e0572-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="e0572-149">-   When a control does not support a requested behavior.</span><span class="sxs-lookup"><span data-stu-id="e0572-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="e0572-150">-   When the parameter is not a valid number.</span><span class="sxs-lookup"><span data-stu-id="e0572-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0572-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0572-151">See also</span></span>

- [<span data-ttu-id="e0572-152">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e0572-152">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="e0572-153">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="e0572-153">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="e0572-154">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="e0572-154">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="e0572-155">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e0572-155">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="e0572-156">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0572-156">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
