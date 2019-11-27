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
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="7be52-102">UI Otomasyonu Pencere Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="7be52-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="7be52-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="7be52-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7be52-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="7be52-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="7be52-105">Bu konu, <xref:System.Windows.Automation.WindowPattern> özellikleri, yöntemleri ve olayları hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IWindowProvider>uygulamak için kılavuz ve kuralları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="7be52-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="7be52-106">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="7be52-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="7be52-107"><xref:System.Windows.Automation.WindowPattern> denetim stili, geleneksel bir grafik kullanıcı arabirimi (GUI) içinde temel pencere tabanlı işlevselliği sağlayan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7be52-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="7be52-108">Bu denetim modelini uygulayan denetimlerin örnekleri, en üst düzey uygulama pencereleri, birden çok belge arabirimi (MDI) alt pencereleri, yeniden boyutlandırılabilir bölünmüş bölme denetimleri, kalıcı iletişim kutuları ve balon yardım pencereleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7be52-108">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="7be52-109">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="7be52-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="7be52-110">Pencere denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7be52-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="7be52-111">UI Otomasyonu kullanarak pencere boyutunu ve ekran konumunu değiştirme özelliğini desteklemek için bir denetimin <xref:System.Windows.Automation.Provider.IWindowProvider>ek olarak <xref:System.Windows.Automation.Provider.ITransformProvider> uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7be52-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="7be52-112"><xref:System.Windows.Automation.Provider.IWindowProvider>uygulamak için genellikle denetimin taşınmasını, yeniden boyutlandırılması, ekranı kaplamış, küçültülmesini veya kapatılmasını sağlayan başlık çubuklarını ve başlık çubuğu öğelerini içeren denetimler.</span><span class="sxs-lookup"><span data-stu-id="7be52-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="7be52-113">Araç ipucu açılır pencereleri ve Birleşik giriş kutusu ya da menü açılan listeleri gibi denetimler genellikle <xref:System.Windows.Automation.Provider.IWindowProvider>uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="7be52-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="7be52-114">Balon yardım pencereleri, bir pencere gibi Kapat düğmesinin sağlanması ile temel araç ipucu açılarından farklılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7be52-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="7be52-115">Tam ekran modu, bir uygulamaya özgü olan ve tipik bir pencere davranışı olmayan IWindowProvider tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7be52-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="7be52-116">IWindowProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="7be52-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="7be52-117">IWindowProvider arabirimi için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7be52-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="7be52-118">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="7be52-118">Required member</span></span>|<span data-ttu-id="7be52-119">Üye türü</span><span class="sxs-lookup"><span data-stu-id="7be52-119">Member type</span></span>|<span data-ttu-id="7be52-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="7be52-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="7be52-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="7be52-121">Property</span></span>|<span data-ttu-id="7be52-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="7be52-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="7be52-123">Property</span></span>|<span data-ttu-id="7be52-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="7be52-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="7be52-125">Property</span></span>|<span data-ttu-id="7be52-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="7be52-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="7be52-127">Property</span></span>|<span data-ttu-id="7be52-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="7be52-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="7be52-129">Property</span></span>|<span data-ttu-id="7be52-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="7be52-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="7be52-131">Property</span></span>|<span data-ttu-id="7be52-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="7be52-133">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7be52-133">Method</span></span>|<span data-ttu-id="7be52-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="7be52-135">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7be52-135">Method</span></span>|<span data-ttu-id="7be52-136">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="7be52-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7be52-137">Method</span></span>|<span data-ttu-id="7be52-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="7be52-139">Olay</span><span class="sxs-lookup"><span data-stu-id="7be52-139">Event</span></span>|<span data-ttu-id="7be52-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="7be52-141">Olay</span><span class="sxs-lookup"><span data-stu-id="7be52-141">Event</span></span>|<span data-ttu-id="7be52-142">Yok.</span><span class="sxs-lookup"><span data-stu-id="7be52-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="7be52-143">Olay</span><span class="sxs-lookup"><span data-stu-id="7be52-143">Event</span></span>|<span data-ttu-id="7be52-144"><xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction> garanti edilmez</span><span class="sxs-lookup"><span data-stu-id="7be52-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="7be52-145">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="7be52-145">Exceptions</span></span>  
 <span data-ttu-id="7be52-146">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7be52-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="7be52-147">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="7be52-147">Exception type</span></span>|<span data-ttu-id="7be52-148">Koşul</span><span class="sxs-lookup"><span data-stu-id="7be52-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="7be52-149">-Bir denetim istenen davranışı desteklemiyorsa.</span><span class="sxs-lookup"><span data-stu-id="7be52-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="7be52-150">-Parametre geçerli bir sayı değil.</span><span class="sxs-lookup"><span data-stu-id="7be52-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7be52-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7be52-151">See also</span></span>

- [<span data-ttu-id="7be52-152">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7be52-152">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="7be52-153">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="7be52-153">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="7be52-154">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="7be52-154">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="7be52-155">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7be52-155">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="7be52-156">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="7be52-156">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
