---
title: UI Otomasyonu Pencere Denetim Düzenini Uygulama
description: Kullanıcı Arabirimi Otomasyonu 'nda pencere denetim modelini uygulamak için yönergeleri ve kuralları gözden geçirin. IWindowProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: b43884393974e6f2863da6a4a5ca8f305e5a160c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286103"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="d2ac5-104">UI Otomasyonu Pencere Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="d2ac5-104">Implementing the UI Automation Window Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="d2ac5-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="d2ac5-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d2ac5-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="d2ac5-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d2ac5-107">Bu konuda <xref:System.Windows.Automation.Provider.IWindowProvider> <xref:System.Windows.Automation.WindowPattern> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="d2ac5-108">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="d2ac5-109"><xref:System.Windows.Automation.WindowPattern>Denetim stili, geleneksel bir grafik kullanıcı arabirimi (GUI) içinde temel pencere tabanlı işlevselliği sağlayan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-109">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="d2ac5-110">Bu denetim modelini uygulayan denetimlerin örnekleri, en üst düzey uygulama pencereleri, birden çok belge arabirimi (MDI) alt pencereleri, yeniden boyutlandırılabilir bölünmüş bölme denetimleri, kalıcı iletişim kutuları ve balon yardım pencereleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-110">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d2ac5-111">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="d2ac5-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="d2ac5-112">Pencere denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d2ac5-112">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="d2ac5-113">UI Otomasyonu kullanarak pencere boyutunu ve ekran konumunu değiştirme özelliğini desteklemek için, bir denetimin buna ek olarak uygulanması gerekir <xref:System.Windows.Automation.Provider.ITransformProvider> <xref:System.Windows.Automation.Provider.IWindowProvider> .</span><span class="sxs-lookup"><span data-stu-id="d2ac5-113">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="d2ac5-114">Denetimin taşınmasını, yeniden boyutlandırılması, büyütülmüş, küçültülmüş veya kapalı olmasını sağlayan başlık çubuklarını ve başlık çubuğu öğelerini içeren denetimler genellikle uygulamak için gereklidir <xref:System.Windows.Automation.Provider.IWindowProvider> .</span><span class="sxs-lookup"><span data-stu-id="d2ac5-114">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="d2ac5-115">Araç ipucu açılır pencereleri ve Birleşik giriş kutusu ya da menü açılır listeleri gibi denetimler genellikle uygulamaz <xref:System.Windows.Automation.Provider.IWindowProvider> .</span><span class="sxs-lookup"><span data-stu-id="d2ac5-115">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="d2ac5-116">Balon yardım pencereleri, bir pencere gibi Kapat düğmesinin sağlanması ile temel araç ipucu açılarından farklılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-116">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="d2ac5-117">Tam ekran modu, bir uygulamaya özgü olan ve tipik bir pencere davranışı olmayan IWindowProvider tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-117">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>

## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="d2ac5-118">IWindowProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="d2ac5-118">Required Members for IWindowProvider</span></span>  

 <span data-ttu-id="d2ac5-119">IWindowProvider arabirimi için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-119">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="d2ac5-120">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="d2ac5-120">Required member</span></span>|<span data-ttu-id="d2ac5-121">Üye türü</span><span class="sxs-lookup"><span data-stu-id="d2ac5-121">Member type</span></span>|<span data-ttu-id="d2ac5-122">Notlar</span><span class="sxs-lookup"><span data-stu-id="d2ac5-122">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="d2ac5-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="d2ac5-123">Property</span></span>|<span data-ttu-id="d2ac5-124">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="d2ac5-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="d2ac5-125">Property</span></span>|<span data-ttu-id="d2ac5-126">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="d2ac5-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="d2ac5-127">Property</span></span>|<span data-ttu-id="d2ac5-128">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="d2ac5-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="d2ac5-129">Property</span></span>|<span data-ttu-id="d2ac5-130">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="d2ac5-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="d2ac5-131">Property</span></span>|<span data-ttu-id="d2ac5-132">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="d2ac5-133">Özellik</span><span class="sxs-lookup"><span data-stu-id="d2ac5-133">Property</span></span>|<span data-ttu-id="d2ac5-134">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="d2ac5-135">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d2ac5-135">Method</span></span>|<span data-ttu-id="d2ac5-136">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="d2ac5-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d2ac5-137">Method</span></span>|<span data-ttu-id="d2ac5-138">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-138">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="d2ac5-139">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d2ac5-139">Method</span></span>|<span data-ttu-id="d2ac5-140">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="d2ac5-141">Olay</span><span class="sxs-lookup"><span data-stu-id="d2ac5-141">Event</span></span>|<span data-ttu-id="d2ac5-142">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="d2ac5-143">Olay</span><span class="sxs-lookup"><span data-stu-id="d2ac5-143">Event</span></span>|<span data-ttu-id="d2ac5-144">Yok</span><span class="sxs-lookup"><span data-stu-id="d2ac5-144">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="d2ac5-145">Olay</span><span class="sxs-lookup"><span data-stu-id="d2ac5-145">Event</span></span>|<span data-ttu-id="d2ac5-146">Garanti edilmez <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="d2ac5-146">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="d2ac5-147">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d2ac5-147">Exceptions</span></span>  

 <span data-ttu-id="d2ac5-148">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-148">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="d2ac5-149">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="d2ac5-149">Exception type</span></span>|<span data-ttu-id="d2ac5-150">Koşul</span><span class="sxs-lookup"><span data-stu-id="d2ac5-150">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="d2ac5-151">-Bir denetim istenen davranışı desteklemiyorsa.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-151">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="d2ac5-152">-Parametre geçerli bir sayı değil.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-152">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2ac5-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2ac5-153">See also</span></span>

- [<span data-ttu-id="d2ac5-154">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d2ac5-154">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="d2ac5-155">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="d2ac5-155">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="d2ac5-156">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="d2ac5-156">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="d2ac5-157">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d2ac5-157">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="d2ac5-158">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="d2ac5-158">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
