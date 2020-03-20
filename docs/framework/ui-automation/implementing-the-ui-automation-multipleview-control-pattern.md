---
title: UI Otomasyon MultipleView Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 9decb617e30a340d3e73e911f7848110de5599e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180165"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="bb66d-102">UI Otomasyon MultipleView Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="bb66d-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="bb66d-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bb66d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bb66d-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="bb66d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bb66d-105">Bu <xref:System.Windows.Automation.Provider.IMultipleViewProvider>konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere, uygulama yönergeleri ve kuralları sunar.</span><span class="sxs-lookup"><span data-stu-id="bb66d-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="bb66d-106">Ek başvurulara bağlantılar konunun sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="bb66d-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="bb66d-107">Denetim <xref:System.Windows.Automation.MultipleViewPattern> deseni, aynı bilgi kümesinin veya alt denetimlerin birden çok temsilini sağlayan ve aralarında geçiş yapan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb66d-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="bb66d-108">Birden çok görünüm sunabilecek denetimlere örnek olarak liste görünümü (içeriğini küçük resimler, döşemeler, simgeler veya ayrıntılar olarak gösterebilen), Microsoft Excel grafikleri (pasta, satır, çubuk, formüllü hücre değeri), Microsoft Word belgeleri (normal, Web düzeni, yazdırma düzen, okuma düzeni, anahat), Microsoft Outlook takvimi (yıl, ay, hafta, gün) ve Microsoft Windows Media Player görünümleri.</span><span class="sxs-lookup"><span data-stu-id="bb66d-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="bb66d-109">Desteklenen görünümler denetim geliştiricisi tarafından belirlenir ve her denetime özgür.</span><span class="sxs-lookup"><span data-stu-id="bb66d-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="bb66d-110">Uygulama Yönergeleri ve Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="bb66d-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="bb66d-111">Çoklu Görünüm denetim deseni uygularken aşağıdaki yönergeleri ve kuralları not edin:</span><span class="sxs-lookup"><span data-stu-id="bb66d-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="bb66d-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>geçerli görünümü sağlayan bir denetimden farklıysa, geçerli görünümü yöneten bir kapsayıcı üzerinde de uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb66d-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="bb66d-113">Örneğin, Windows Gezgini geçerli klasör içeriği için bir Liste denetimi içerirken, denetim görünümü Windows Gezgini uygulamasından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="bb66d-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="bb66d-114">İçeriğini sıralayabilen bir denetim, birden çok görünümü desteklemek için kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="bb66d-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="bb66d-115">Görünümler topluluğu örnekler arasında aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb66d-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="bb66d-116">Görünüm adları Metinden Konuşmaya, Braille'de ve diğer insan tarafından okunabilir uygulamalarda kullanıma uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb66d-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="bb66d-117">IMultipleViewProvider için Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="bb66d-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="bb66d-118">IMultipleViewProvider'ı uygulamak için aşağıdaki özellikler ve yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bb66d-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="bb66d-119">Gerekli üyeler</span><span class="sxs-lookup"><span data-stu-id="bb66d-119">Required members</span></span>|<span data-ttu-id="bb66d-120">Üye tipi</span><span class="sxs-lookup"><span data-stu-id="bb66d-120">Member type</span></span>|<span data-ttu-id="bb66d-121">Notlar</span><span class="sxs-lookup"><span data-stu-id="bb66d-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="bb66d-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="bb66d-122">Property</span></span>|<span data-ttu-id="bb66d-123">None</span><span class="sxs-lookup"><span data-stu-id="bb66d-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="bb66d-124">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb66d-124">Method</span></span>|<span data-ttu-id="bb66d-125">None</span><span class="sxs-lookup"><span data-stu-id="bb66d-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="bb66d-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb66d-126">Method</span></span>|<span data-ttu-id="bb66d-127">None</span><span class="sxs-lookup"><span data-stu-id="bb66d-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="bb66d-128">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bb66d-128">Method</span></span>|<span data-ttu-id="bb66d-129">None</span><span class="sxs-lookup"><span data-stu-id="bb66d-129">None</span></span>|  
  
 <span data-ttu-id="bb66d-130">Bu denetim deseniyle ilişkili olaylar yok.</span><span class="sxs-lookup"><span data-stu-id="bb66d-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="bb66d-131">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bb66d-131">Exceptions</span></span>  
 <span data-ttu-id="bb66d-132">Sağlayıcı aşağıdaki özel durumları atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb66d-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="bb66d-133">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="bb66d-133">Exception type</span></span>|<span data-ttu-id="bb66d-134">Koşul</span><span class="sxs-lookup"><span data-stu-id="bb66d-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="bb66d-135">Desteklenen <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> görünümler koleksiyonunun üyesi olmayan bir parametre yle çağrıldığınızda. <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A></span><span class="sxs-lookup"><span data-stu-id="bb66d-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb66d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb66d-136">See also</span></span>

- [<span data-ttu-id="bb66d-137">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bb66d-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="bb66d-138">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="bb66d-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="bb66d-139">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="bb66d-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="bb66d-140">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bb66d-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="bb66d-141">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="bb66d-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
