---
title: "UI Otomasyon MultipleView Denetim Düzeni Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
caps.latest.revision: "15"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 899f260dfef1d1e28a5a3605de772cdb7d358b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="94a12-102">UI Otomasyon MultipleView Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="94a12-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="94a12-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="94a12-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="94a12-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="94a12-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="94a12-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, olayları ve özellikleri hakkındaki bilgileri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="94a12-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="94a12-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="94a12-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="94a12-107"><xref:System.Windows.Automation.MultipleViewPattern> Denetim düzeni sağlayan ve birden çok bilgi veya alt denetimleri aynı kümesini gösterimlerini, arasında geçiş yapabilir denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94a12-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="94a12-108">Örnekler birden çok görünüm sunabilirsiniz denetimlerinizin (hangi içeriğinin küçük resimleri, kutucukları, simgeler veya ayrıntılar gösterebilir) liste görünümü [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafikleri (pasta, satır, çubuğu, hücre değerini bir formülü olan), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] belgeleri (normal, Web düzeni yazdırma düzeni, okuma düzeni, anahat), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] Takvim (yıl, ay, hafta, gün), ve [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] kaplamaları.</span><span class="sxs-lookup"><span data-stu-id="94a12-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="94a12-109">Desteklenen görünümler denetim geliştirici tarafından belirlenir ve her denetim için özeldir.</span><span class="sxs-lookup"><span data-stu-id="94a12-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="94a12-110">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="94a12-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="94a12-111">Birden çok görünüm denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="94a12-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="94a12-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>Ayrıca geçerli görünümü sağlayan denetimden farklıysa, geçerli görünümü yöneten bir kapsayıcısı üzerinde uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94a12-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="94a12-113">Örneğin, denetimin görünümünü Windows Explorer uygulamasından yönetilen sırasında Windows Explorer geçerli klasör içerik için bir liste denetimini içerir.</span><span class="sxs-lookup"><span data-stu-id="94a12-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
-   <span data-ttu-id="94a12-114">İçeriğini sıralama yapabiliyor bir denetim, birden çok görünüm desteklemek için dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="94a12-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
-   <span data-ttu-id="94a12-115">Görünümler koleksiyonu örneklerinde aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94a12-115">The collection of views must be identical across instances.</span></span>  
  
-   <span data-ttu-id="94a12-116">Görünüm adları metin okuma, Braille ve diğer okunabilir uygulamaları kullanmak için uygun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="94a12-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="94a12-117">Gerekli üyeleri IMultipleViewProvider için</span><span class="sxs-lookup"><span data-stu-id="94a12-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="94a12-118">Aşağıdaki özellikleri ve yöntemleri IMultipleViewProvider uygulamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="94a12-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="94a12-119">Gerekli üyeleri</span><span class="sxs-lookup"><span data-stu-id="94a12-119">Required members</span></span>|<span data-ttu-id="94a12-120">Üye türü</span><span class="sxs-lookup"><span data-stu-id="94a12-120">Member type</span></span>|<span data-ttu-id="94a12-121">Notlar</span><span class="sxs-lookup"><span data-stu-id="94a12-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="94a12-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="94a12-122">Property</span></span>|<span data-ttu-id="94a12-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="94a12-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="94a12-124">Yöntem</span><span class="sxs-lookup"><span data-stu-id="94a12-124">Method</span></span>|<span data-ttu-id="94a12-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="94a12-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="94a12-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="94a12-126">Method</span></span>|<span data-ttu-id="94a12-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="94a12-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="94a12-128">Yöntem</span><span class="sxs-lookup"><span data-stu-id="94a12-128">Method</span></span>|<span data-ttu-id="94a12-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="94a12-129">None</span></span>|  
  
 <span data-ttu-id="94a12-130">Bu denetim düzeni ile ilişkili olay yok.</span><span class="sxs-lookup"><span data-stu-id="94a12-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="94a12-131">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="94a12-131">Exceptions</span></span>  
 <span data-ttu-id="94a12-132">Sağlayıcı, aşağıdaki özel durumlar oluşturma gerekir.</span><span class="sxs-lookup"><span data-stu-id="94a12-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="94a12-133">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="94a12-133">Exception type</span></span>|<span data-ttu-id="94a12-134">Koşul</span><span class="sxs-lookup"><span data-stu-id="94a12-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="94a12-135">Zaman da <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> veya <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> desteklenen görünümler koleksiyonunun bir üyesi olmayan bir parametre olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="94a12-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94a12-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94a12-136">See Also</span></span>  
 [<span data-ttu-id="94a12-137">UI Otomasyon denetim düzenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="94a12-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="94a12-138">UI Otomasyon sağlayıcısında denetim düzenleri desteği</span><span class="sxs-lookup"><span data-stu-id="94a12-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="94a12-139">İstemciler için UI Otomasyon denetim düzenleri</span><span class="sxs-lookup"><span data-stu-id="94a12-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="94a12-140">UI Otomasyon ağacına genel bakış</span><span class="sxs-lookup"><span data-stu-id="94a12-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="94a12-141">UI otomasyonda önbelleğe almayı kullanma</span><span class="sxs-lookup"><span data-stu-id="94a12-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
