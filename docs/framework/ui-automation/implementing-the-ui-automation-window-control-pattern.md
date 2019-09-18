---
title: UI Otomasyonu Pencere Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: ad2f84fbde512bb99b213bf3b97f2190091d8576
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042985"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="6d6e8-102">UI Otomasyonu Pencere Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="6d6e8-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="6d6e8-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6d6e8-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="6d6e8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="6d6e8-105">Bu konuda özellikler, Yöntemler ve olaylar hakkında <xref:System.Windows.Automation.Provider.IWindowProvider> <xref:System.Windows.Automation.WindowPattern> bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="6d6e8-106">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="6d6e8-107"><xref:System.Windows.Automation.WindowPattern> Denetim stili, geleneksel bir grafik kullanıcı arabirimi (GUI) içinde temel pencere tabanlı işlevselliği sağlayan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="6d6e8-108">Bu denetim modelini uygulayan denetimlerin örnekleri, en üst düzey uygulama pencereleri, birden çok belge arabirimi (MDI) alt pencereleri, yeniden boyutlandırılabilir bölünmüş bölme denetimleri, kalıcı iletişim kutuları ve balon yardım pencereleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-108">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="6d6e8-109">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="6d6e8-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="6d6e8-110">Pencere denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6d6e8-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="6d6e8-111">UI Otomasyonu kullanarak pencere boyutunu ve ekran konumunu değiştirme özelliğini desteklemek için, bir denetimin <xref:System.Windows.Automation.Provider.ITransformProvider> <xref:System.Windows.Automation.Provider.IWindowProvider>buna ek olarak uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="6d6e8-112">Denetimin taşınmasını, yeniden boyutlandırılması, büyütülmüş, küçültülmüş veya kapalı olmasını sağlayan başlık çubuklarını ve başlık çubuğu öğelerini içeren denetimler genellikle uygulamak <xref:System.Windows.Automation.Provider.IWindowProvider>için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="6d6e8-113">Araç ipucu açılır pencereleri ve Birleşik giriş kutusu ya da menü açılır listeleri gibi denetimler genellikle uygulamaz <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="6d6e8-114">Balon yardım pencereleri, bir pencere gibi Kapat düğmesinin sağlanması ile temel araç ipucu açılarından farklılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="6d6e8-115">Tam ekran modu, bir uygulamaya özgü olan ve tipik bir pencere davranışı olmayan IWindowProvider tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="6d6e8-116">IWindowProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="6d6e8-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="6d6e8-117">IWindowProvider arabirimi için aşağıdaki özellikler, Yöntemler ve olaylar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="6d6e8-118">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="6d6e8-118">Required member</span></span>|<span data-ttu-id="6d6e8-119">Üye türü</span><span class="sxs-lookup"><span data-stu-id="6d6e8-119">Member type</span></span>|<span data-ttu-id="6d6e8-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="6d6e8-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="6d6e8-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="6d6e8-121">Property</span></span>|<span data-ttu-id="6d6e8-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="6d6e8-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="6d6e8-123">Property</span></span>|<span data-ttu-id="6d6e8-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="6d6e8-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="6d6e8-125">Property</span></span>|<span data-ttu-id="6d6e8-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="6d6e8-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="6d6e8-127">Property</span></span>|<span data-ttu-id="6d6e8-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="6d6e8-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="6d6e8-129">Property</span></span>|<span data-ttu-id="6d6e8-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="6d6e8-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="6d6e8-131">Property</span></span>|<span data-ttu-id="6d6e8-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="6d6e8-133">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6d6e8-133">Method</span></span>|<span data-ttu-id="6d6e8-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="6d6e8-135">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6d6e8-135">Method</span></span>|<span data-ttu-id="6d6e8-136">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="6d6e8-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6d6e8-137">Method</span></span>|<span data-ttu-id="6d6e8-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="6d6e8-139">Olay</span><span class="sxs-lookup"><span data-stu-id="6d6e8-139">Event</span></span>|<span data-ttu-id="6d6e8-140">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="6d6e8-141">Olay</span><span class="sxs-lookup"><span data-stu-id="6d6e8-141">Event</span></span>|<span data-ttu-id="6d6e8-142">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="6d6e8-143">Olay</span><span class="sxs-lookup"><span data-stu-id="6d6e8-143">Event</span></span>|<span data-ttu-id="6d6e8-144">Garanti edilmez<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="6d6e8-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="6d6e8-145">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="6d6e8-145">Exceptions</span></span>  
 <span data-ttu-id="6d6e8-146">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="6d6e8-147">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="6d6e8-147">Exception type</span></span>|<span data-ttu-id="6d6e8-148">Koşul</span><span class="sxs-lookup"><span data-stu-id="6d6e8-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="6d6e8-149">-Bir denetim istenen davranışı desteklemiyorsa.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="6d6e8-150">-Parametre geçerli bir sayı değil.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d6e8-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d6e8-151">See also</span></span>

- [<span data-ttu-id="6d6e8-152">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6d6e8-152">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="6d6e8-153">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="6d6e8-153">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="6d6e8-154">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="6d6e8-154">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="6d6e8-155">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6d6e8-155">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="6d6e8-156">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="6d6e8-156">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
