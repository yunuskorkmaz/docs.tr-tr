---
title: "UI Otomasyonu Pencere Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9e8d83c3ef40ccc6e97ba3128cab5d88a5af5305
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="fe400-102">UI Otomasyonu Pencere Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="fe400-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="fe400-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="fe400-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fe400-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="fe400-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="fe400-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IWindowProvider>, ilgili bilgiler dahil olmak üzere <xref:System.Windows.Automation.WindowPattern> özellikleri, yöntemleri ve olaylar.</span><span class="sxs-lookup"><span data-stu-id="fe400-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="fe400-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe400-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="fe400-107"><xref:System.Windows.Automation.WindowPattern> Denetim düzeni içinde geleneksel Windows tabanlı temel işlevleri sağlayan denetimleri desteklemek için kullanılan [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe400-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span></span> <span data-ttu-id="fe400-108">Bu denetim düzeni uygulamalıdır denetimleri örnekleri arasında en üst düzey uygulama windows [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] alt öğe pencerelerini, yeniden boyutlandırılabilir bölünmüş bölmesi denetimlerinin, kalıcı iletişim kutuları ve balon windows yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="fe400-108">Examples of controls that must implement this control pattern include top-level application windows, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="fe400-109">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="fe400-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="fe400-110">Pencere denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="fe400-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="fe400-111">UI Otomasyonu kullanarak konumu ekran ve her iki pencere boyutunu değiştirmek için yeteneğini desteklemek için bir denetim uygulamalıdır <xref:System.Windows.Automation.Provider.ITransformProvider> ek olarak <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="fe400-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="fe400-112">Başlık çubukları ve taşınmasına izin denetimini değişirse ekranı, etkinleştirme başlık çubuğu öğeleri içeren denetimler küçültülebilir ya da kapalı uygulamak için genellikle gereken <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="fe400-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="fe400-113">Araç İpucu açılır pencereleri ve birleşik giriş kutusu veya menü aşağı açılan listeler gibi denetimleri genellikle uygulamaz <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="fe400-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="fe400-114">Balon Yardım windows temel araç ipucu pencerelere penceresi benzeri Kapat düğmesi sağlama tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="fe400-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
-   <span data-ttu-id="fe400-115">Tam ekran modu özelliğe özgü olduğu gibi IWindowProvider tarafından desteklenmiyor uygulamaya ve tipik penceresi davranış değildir.</span><span class="sxs-lookup"><span data-stu-id="fe400-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="fe400-116">Gerekli üyeleri IWindowProvider için</span><span class="sxs-lookup"><span data-stu-id="fe400-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="fe400-117">Aşağıdaki özellikleri, yöntemleri ve olayları IWindowProvider arabirim için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fe400-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="fe400-118">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="fe400-118">Required member</span></span>|<span data-ttu-id="fe400-119">Üye türü</span><span class="sxs-lookup"><span data-stu-id="fe400-119">Member type</span></span>|<span data-ttu-id="fe400-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="fe400-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="fe400-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="fe400-121">Property</span></span>|<span data-ttu-id="fe400-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="fe400-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="fe400-123">Property</span></span>|<span data-ttu-id="fe400-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="fe400-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="fe400-125">Property</span></span>|<span data-ttu-id="fe400-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="fe400-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="fe400-127">Property</span></span>|<span data-ttu-id="fe400-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="fe400-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="fe400-129">Property</span></span>|<span data-ttu-id="fe400-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="fe400-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="fe400-131">Property</span></span>|<span data-ttu-id="fe400-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="fe400-133">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe400-133">Method</span></span>|<span data-ttu-id="fe400-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="fe400-135">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe400-135">Method</span></span>|<span data-ttu-id="fe400-136">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="fe400-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe400-137">Method</span></span>|<span data-ttu-id="fe400-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="fe400-139">Olay</span><span class="sxs-lookup"><span data-stu-id="fe400-139">Event</span></span>|<span data-ttu-id="fe400-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="fe400-141">Olay</span><span class="sxs-lookup"><span data-stu-id="fe400-141">Event</span></span>|<span data-ttu-id="fe400-142">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe400-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="fe400-143">Olay</span><span class="sxs-lookup"><span data-stu-id="fe400-143">Event</span></span>|<span data-ttu-id="fe400-144">Olması garanti edilmez<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="fe400-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="fe400-145">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="fe400-145">Exceptions</span></span>  
 <span data-ttu-id="fe400-146">Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe400-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="fe400-147">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="fe400-147">Exception type</span></span>|<span data-ttu-id="fe400-148">Koşul</span><span class="sxs-lookup"><span data-stu-id="fe400-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="fe400-149">-Ne zaman bir denetim istenen davranışını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fe400-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="fe400-150">-Zaman parametresi geçerli bir sayı değil.</span><span class="sxs-lookup"><span data-stu-id="fe400-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe400-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe400-151">See Also</span></span>  
 [<span data-ttu-id="fe400-152">UI Otomasyon denetim düzenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="fe400-152">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="fe400-153">UI Otomasyon sağlayıcısında denetim düzenleri desteği</span><span class="sxs-lookup"><span data-stu-id="fe400-153">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="fe400-154">İstemciler için UI Otomasyon denetim düzenleri</span><span class="sxs-lookup"><span data-stu-id="fe400-154">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="fe400-155">UI Otomasyon ağacına genel bakış</span><span class="sxs-lookup"><span data-stu-id="fe400-155">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="fe400-156">UI otomasyonda önbelleğe almayı kullanma</span><span class="sxs-lookup"><span data-stu-id="fe400-156">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
