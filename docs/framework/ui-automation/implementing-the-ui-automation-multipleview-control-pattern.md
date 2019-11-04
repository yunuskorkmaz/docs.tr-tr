---
title: UI Otomasyon MultipleView Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 62f0ba1dc8b7836a3b4699699b91b567eb8051f3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458185"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="bc812-102">UI Otomasyon MultipleView Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="bc812-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="bc812-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="bc812-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bc812-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="bc812-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bc812-105">Bu konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IMultipleViewProvider>uygulamak için kılavuz ve kuralları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="bc812-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="bc812-106">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bc812-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="bc812-107"><xref:System.Windows.Automation.MultipleViewPattern> denetim stili, aynı bilgi kümesinin veya alt denetimlerin birden çok temsilini sağlayan ve arasında geçiş yapabilecek denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc812-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="bc812-108">Birden çok görünüm sunan denetimlerin örnekleri, liste görünümünü (içeriğini küçük resimler, Kutucuklar, simgeler veya ayrıntılar olarak gösterebilir), Microsoft Excel grafikleri (pasta, çizgi, çubuk, formül içeren hücre değeri), Microsoft Word belgeleri (normal, Web düzeni, Yazdır) içerir. Düzen, okuma düzeni, ana hat), Microsoft Outlook Takvim (yıl, ay, hafta, gün) ve Microsoft Windows Media Player dış görünümleri.</span><span class="sxs-lookup"><span data-stu-id="bc812-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="bc812-109">Desteklenen görünümler denetim geliştiricisi tarafından belirlenir ve her denetime özeldir.</span><span class="sxs-lookup"><span data-stu-id="bc812-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="bc812-110">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="bc812-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="bc812-111">Birden çok görünüm denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bc812-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="bc812-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider>, geçerli görünümü sağlayan bir denetimden farklıysa geçerli görünümü yöneten bir kapsayıcıya de uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc812-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="bc812-113">Örneğin, Windows Gezgini, denetimin görünümü Windows Gezgini uygulamasından yönetilirken, geçerli klasör içeriği için bir liste denetimi içerir.</span><span class="sxs-lookup"><span data-stu-id="bc812-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="bc812-114">İçeriğini sıralayacak bir denetim, birden fazla görünümü destekleyecek şekilde değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="bc812-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="bc812-115">Görünümler koleksiyonu örneklerin tamamında aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc812-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="bc812-116">Görünüm adları Metin Okuma, Braille ve diğer insan tarafından okunabilen uygulamalarda kullanım için uygun olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc812-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="bc812-117">IMultipleViewProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="bc812-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="bc812-118">IMultipleViewProvider uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bc812-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="bc812-119">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="bc812-119">Required members</span></span>|<span data-ttu-id="bc812-120">Üye türü</span><span class="sxs-lookup"><span data-stu-id="bc812-120">Member type</span></span>|<span data-ttu-id="bc812-121">Notlar</span><span class="sxs-lookup"><span data-stu-id="bc812-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="bc812-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="bc812-122">Property</span></span>|<span data-ttu-id="bc812-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc812-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="bc812-124">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bc812-124">Method</span></span>|<span data-ttu-id="bc812-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc812-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="bc812-126">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bc812-126">Method</span></span>|<span data-ttu-id="bc812-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc812-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="bc812-128">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bc812-128">Method</span></span>|<span data-ttu-id="bc812-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="bc812-129">None</span></span>|  
  
 <span data-ttu-id="bc812-130">Bu denetim düzeniyle ilişkili hiçbir olay yok.</span><span class="sxs-lookup"><span data-stu-id="bc812-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="bc812-131">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="bc812-131">Exceptions</span></span>  
 <span data-ttu-id="bc812-132">Sağlayıcı aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc812-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="bc812-133">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="bc812-133">Exception type</span></span>|<span data-ttu-id="bc812-134">Koşul</span><span class="sxs-lookup"><span data-stu-id="bc812-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="bc812-135"><xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ya da <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>, desteklenen görünümler koleksiyonunun üyesi olmayan bir parametre ile çağrıldığında.</span><span class="sxs-lookup"><span data-stu-id="bc812-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc812-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc812-136">See also</span></span>

- [<span data-ttu-id="bc812-137">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc812-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="bc812-138">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="bc812-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="bc812-139">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="bc812-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="bc812-140">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc812-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="bc812-141">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="bc812-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
