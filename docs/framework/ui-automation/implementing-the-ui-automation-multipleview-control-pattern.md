---
title: UI Otomasyon MultipleView Denetim Düzeni Uygulama
description: Kullanıcı Arabirimi Otomasyonu 'nda MultipleView denetim modelini uygulamak için yönergeleri ve kuralları gözden geçirin. IMultipleViewProvider arabirimi için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 0d65d57637891fcb1307f5ee83a417941ff323fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168225"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="361bd-104">UI Otomasyon MultipleView Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="361bd-104">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="361bd-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="361bd-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="361bd-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="361bd-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="361bd-107">Bu konu <xref:System.Windows.Automation.Provider.IMultipleViewProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="361bd-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="361bd-108">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="361bd-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="361bd-109"><xref:System.Windows.Automation.MultipleViewPattern>Denetim stili, aynı bilgi kümesinin veya alt denetimlerin birden çok temsilini sağlayan ve arasında geçiş yapabilecek denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="361bd-109">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="361bd-110">Birden çok görünüm sunan denetimlerin örnekleri, liste görünümünü içerir (Bu, içeriğini küçük resim olarak gösterebilir) Kutucuklar, simgeler veya Ayrıntılar), Microsoft Excel grafikleri (pasta, çizgi, çubuk, formül içeren hücre değeri), Microsoft Word belgeleri (normal, Web düzeni, yazdırma düzeni, okuma düzeni, ana hat), Microsoft Outlook Takvim (year, month, Week, Day) ve Microsoft Windows Media Player kaplamaları.</span><span class="sxs-lookup"><span data-stu-id="361bd-110">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="361bd-111">Desteklenen görünümler denetim geliştiricisi tarafından belirlenir ve her denetime özeldir.</span><span class="sxs-lookup"><span data-stu-id="361bd-111">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="361bd-112">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="361bd-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="361bd-113">Birden çok görünüm denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="361bd-113">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="361bd-114"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>geçerli görünümü sağlayan bir denetimden farklıysa geçerli görünümü yöneten bir kapsayıcıya de uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="361bd-114"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="361bd-115">Örneğin, Windows Gezgini, denetimin görünümü Windows Gezgini uygulamasından yönetilirken, geçerli klasör içeriği için bir liste denetimi içerir.</span><span class="sxs-lookup"><span data-stu-id="361bd-115">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="361bd-116">İçeriğini sıralayacak bir denetim, birden fazla görünümü destekleyecek şekilde değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="361bd-116">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="361bd-117">Görünümler koleksiyonu örneklerin tamamında aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="361bd-117">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="361bd-118">Görünüm adları Metin Okuma, Braille ve diğer insan tarafından okunabilen uygulamalarda kullanım için uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="361bd-118">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="361bd-119">IMultipleViewProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="361bd-119">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="361bd-120">IMultipleViewProvider uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="361bd-120">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="361bd-121">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="361bd-121">Required members</span></span>|<span data-ttu-id="361bd-122">Üye türü</span><span class="sxs-lookup"><span data-stu-id="361bd-122">Member type</span></span>|<span data-ttu-id="361bd-123">Notlar</span><span class="sxs-lookup"><span data-stu-id="361bd-123">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="361bd-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="361bd-124">Property</span></span>|<span data-ttu-id="361bd-125">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="361bd-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="361bd-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="361bd-126">Method</span></span>|<span data-ttu-id="361bd-127">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="361bd-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="361bd-128">Yöntem</span><span class="sxs-lookup"><span data-stu-id="361bd-128">Method</span></span>|<span data-ttu-id="361bd-129">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="361bd-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="361bd-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="361bd-130">Method</span></span>|<span data-ttu-id="361bd-131">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="361bd-131">None</span></span>|  
  
 <span data-ttu-id="361bd-132">Bu denetim düzeniyle ilişkili hiçbir olay yok.</span><span class="sxs-lookup"><span data-stu-id="361bd-132">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="361bd-133">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="361bd-133">Exceptions</span></span>  
 <span data-ttu-id="361bd-134">Sağlayıcı aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="361bd-134">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="361bd-135">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="361bd-135">Exception type</span></span>|<span data-ttu-id="361bd-136">Koşul</span><span class="sxs-lookup"><span data-stu-id="361bd-136">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="361bd-137">Ya da <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> Desteklenen görünümler koleksiyonunun üyesi olmayan bir parametre ile çağrıldığında.</span><span class="sxs-lookup"><span data-stu-id="361bd-137">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="361bd-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="361bd-138">See also</span></span>

- [<span data-ttu-id="361bd-139">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="361bd-139">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="361bd-140">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="361bd-140">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="361bd-141">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="361bd-141">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="361bd-142">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="361bd-142">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="361bd-143">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="361bd-143">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
