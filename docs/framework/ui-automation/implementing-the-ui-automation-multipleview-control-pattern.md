---
title: UI Otomasyon MultipleView Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 777f529b3b925a965b24cf1a4b38b9d3b9adae7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408385"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="cbcfc-102">UI Otomasyon MultipleView Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="cbcfc-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="cbcfc-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cbcfc-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="cbcfc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="cbcfc-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, olayları ve özellikleri hakkındaki bilgileri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="cbcfc-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="cbcfc-107"><xref:System.Windows.Automation.MultipleViewPattern> Denetim düzeni sağlayan ve birden çok bilgi veya alt denetimleri aynı kümesini gösterimlerini, arasında geçiş yapabilir denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="cbcfc-108">Örnekler birden çok görünüm sunabilirsiniz denetimlerinizin (hangi içeriğinin küçük resimleri, kutucukları, simgeler veya ayrıntılar gösterebilir) liste görünümü [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafikleri (pasta, satır, çubuğu, hücre değerini bir formülü olan), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] belgeleri (normal, Web düzeni yazdırma düzeni, okuma düzeni, anahat), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] Takvim (yıl, ay, hafta, gün), ve [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] kaplamaları.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="cbcfc-109">Desteklenen görünümler denetim geliştirici tarafından belirlenir ve her denetim için özeldir.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="cbcfc-110">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="cbcfc-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="cbcfc-111">Birden çok görünüm denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="cbcfc-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="cbcfc-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> Ayrıca geçerli görünümü sağlayan denetimden farklıysa, geçerli görünümü yöneten bir kapsayıcısı üzerinde uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="cbcfc-113">Örneğin, denetimin görünümünü Windows Explorer uygulamasından yönetilen sırasında Windows Explorer geçerli klasör içerik için bir liste denetimini içerir.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
-   <span data-ttu-id="cbcfc-114">İçeriğini sıralama yapabiliyor bir denetim, birden çok görünüm desteklemek için dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
-   <span data-ttu-id="cbcfc-115">Görünümler koleksiyonu örneklerinde aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-115">The collection of views must be identical across instances.</span></span>  
  
-   <span data-ttu-id="cbcfc-116">Görünüm adları metin okuma, Braille ve diğer okunabilir uygulamaları kullanmak için uygun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="cbcfc-117">Gerekli üyeleri IMultipleViewProvider için</span><span class="sxs-lookup"><span data-stu-id="cbcfc-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="cbcfc-118">Aşağıdaki özellikleri ve yöntemleri IMultipleViewProvider uygulamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="cbcfc-119">Gerekli üyeleri</span><span class="sxs-lookup"><span data-stu-id="cbcfc-119">Required members</span></span>|<span data-ttu-id="cbcfc-120">Üye türü</span><span class="sxs-lookup"><span data-stu-id="cbcfc-120">Member type</span></span>|<span data-ttu-id="cbcfc-121">Notlar</span><span class="sxs-lookup"><span data-stu-id="cbcfc-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="cbcfc-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="cbcfc-122">Property</span></span>|<span data-ttu-id="cbcfc-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="cbcfc-124">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cbcfc-124">Method</span></span>|<span data-ttu-id="cbcfc-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="cbcfc-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cbcfc-126">Method</span></span>|<span data-ttu-id="cbcfc-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="cbcfc-128">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cbcfc-128">Method</span></span>|<span data-ttu-id="cbcfc-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-129">None</span></span>|  
  
 <span data-ttu-id="cbcfc-130">Bu denetim düzeni ile ilişkili olay yok.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="cbcfc-131">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="cbcfc-131">Exceptions</span></span>  
 <span data-ttu-id="cbcfc-132">Sağlayıcı, aşağıdaki özel durumlar oluşturma gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="cbcfc-133">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="cbcfc-133">Exception type</span></span>|<span data-ttu-id="cbcfc-134">Koşul</span><span class="sxs-lookup"><span data-stu-id="cbcfc-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="cbcfc-135">Zaman da <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> veya <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> desteklenen görünümler koleksiyonunun bir üyesi olmayan bir parametre olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbcfc-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbcfc-136">See Also</span></span>  
 [<span data-ttu-id="cbcfc-137">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cbcfc-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="cbcfc-138">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="cbcfc-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="cbcfc-139">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="cbcfc-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="cbcfc-140">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cbcfc-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="cbcfc-141">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="cbcfc-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
