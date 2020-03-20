---
title: UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: b1213791609245209fa37e3cdcb0876c963bfeb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180200"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="af0ff-102">UI Otomasyon Yerleştirme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="af0ff-102">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="af0ff-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="af0ff-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="af0ff-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="af0ff-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="af0ff-105">Bu <xref:System.Windows.Automation.Provider.IDockProvider>konu, özellikler hakkında bilgi de dahil olmak üzere uygulama yönergeleri ve kuralları sunar.</span><span class="sxs-lookup"><span data-stu-id="af0ff-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="af0ff-106">Ek başvurulara bağlantılar konunun sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="af0ff-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="af0ff-107">Denetim <xref:System.Windows.Automation.DockPattern> deseni, bir yerleştirme kapsayıcısı içindeki bir denetimin dock özelliklerini ortaya çıkarmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af0ff-107">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="af0ff-108">Yerleştirme kapsayıcısı, alt öğeleri birbirine göre yatay ve dikey olarak düzenlemenizi sağlayan bir denetimdir.</span><span class="sxs-lookup"><span data-stu-id="af0ff-108">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="af0ff-109">Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="af0ff-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="af0ff-110">![İki kenetlenmiş çocukla kenetlenmiş konteynır.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="af0ff-110">![Docking container with two docked children.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="af0ff-111">"Sınıf Görünümü" Penceresinin DockPosition.Right ve "Hata Listesi" Penceresinin DockPosition olduğu Visual Studio'dan Yerleştirme Örneği.Alt</span><span class="sxs-lookup"><span data-stu-id="af0ff-111">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="af0ff-112">Uygulama Yönergeleri ve Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="af0ff-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="af0ff-113">Dock denetim modelini uygularken aşağıdaki yönergeleri ve kuralları dikkate alabelirtin:</span><span class="sxs-lookup"><span data-stu-id="af0ff-113">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="af0ff-114"><xref:System.Windows.Automation.Provider.IDockProvider>yerleştirme kabının herhangi bir özelliğini veya yerleştirme kabı içindeki geçerli denetime bitişik olarak sabitlenmiş denetimlerin özelliklerini ortaya çıkarmaz.</span><span class="sxs-lookup"><span data-stu-id="af0ff-114"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
- <span data-ttu-id="af0ff-115">Denetimler, geçerli z sıralarına göre birbirine göre sabitlenir; z-sıra yerleşimleri ne kadar yüksekse, yerleştirme kabının belirtilen kenarından o kadar uzağa yerleştirilirler.</span><span class="sxs-lookup"><span data-stu-id="af0ff-115">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
- <span data-ttu-id="af0ff-116">Yerleştirme kapsayıcısı yeniden boyutlandırılırsa, konteyneriçindeki sabitlenmiş denetimler, ilk olarak sabitlendikleri kenarına yeniden konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="af0ff-116">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="af0ff-117">Kenetlenmiş denetimler de kendi <xref:System.Windows.Automation.DockPosition>yerleştirme davranışına göre kapsayıcı içinde herhangi bir alanı doldurmak için yeniden boyutlandırAcak .</span><span class="sxs-lookup"><span data-stu-id="af0ff-117">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="af0ff-118">Örneğin, <xref:System.Windows.Automation.DockPosition.Top> belirtilirse, denetimin sol ve sağ tarafları kullanılabilir alanı doldurmak için genişler.</span><span class="sxs-lookup"><span data-stu-id="af0ff-118">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="af0ff-119"><xref:System.Windows.Automation.DockPosition.Fill> Belirtilirse, denetimin dört tarafı kullanılabilir alanı doldurmak için genişler.</span><span class="sxs-lookup"><span data-stu-id="af0ff-119">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
- <span data-ttu-id="af0ff-120">Çoklu monitör sisteminde, denetimler geçerli monitörün sol veya sağ tarafına dock gerekir.</span><span class="sxs-lookup"><span data-stu-id="af0ff-120">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="af0ff-121">Bu mümkün değilse, en soldaki monitörün sol tarafına veya en sağdaki monitörün sağ tarafına dock gerekir.</span><span class="sxs-lookup"><span data-stu-id="af0ff-121">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="af0ff-122">IDockProvider için Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="af0ff-122">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="af0ff-123">IDockProvider arabiriminin uygulanması için aşağıdaki özellikler ve yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="af0ff-123">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="af0ff-124">Gerekli üyeler</span><span class="sxs-lookup"><span data-stu-id="af0ff-124">Required members</span></span>|<span data-ttu-id="af0ff-125">Üye tipi</span><span class="sxs-lookup"><span data-stu-id="af0ff-125">Member type</span></span>|<span data-ttu-id="af0ff-126">Notlar</span><span class="sxs-lookup"><span data-stu-id="af0ff-126">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="af0ff-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="af0ff-127">Property</span></span>|<span data-ttu-id="af0ff-128">None</span><span class="sxs-lookup"><span data-stu-id="af0ff-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="af0ff-129">Yöntem</span><span class="sxs-lookup"><span data-stu-id="af0ff-129">Method</span></span>|<span data-ttu-id="af0ff-130">None</span><span class="sxs-lookup"><span data-stu-id="af0ff-130">None</span></span>|  
  
 <span data-ttu-id="af0ff-131">Bu denetim deseni ilişkili olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="af0ff-131">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="af0ff-132">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="af0ff-132">Exceptions</span></span>  
 <span data-ttu-id="af0ff-133">Sağlayıcılar aşağıdaki özel durumları atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af0ff-133">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="af0ff-134">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="af0ff-134">Exception type</span></span>|<span data-ttu-id="af0ff-135">Koşul</span><span class="sxs-lookup"><span data-stu-id="af0ff-135">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="af0ff-136">- Bir denetim istenen dock stilini yürütemediğinde.</span><span class="sxs-lookup"><span data-stu-id="af0ff-136">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af0ff-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af0ff-137">See also</span></span>

- [<span data-ttu-id="af0ff-138">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="af0ff-138">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="af0ff-139">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="af0ff-139">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="af0ff-140">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="af0ff-140">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="af0ff-141">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="af0ff-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="af0ff-142">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="af0ff-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
