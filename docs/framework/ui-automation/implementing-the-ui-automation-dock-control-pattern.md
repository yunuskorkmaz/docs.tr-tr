---
title: UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 1e2084483a34709392b9d3ceab02472c36944132
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435440"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="5cbf7-102">UI Otomasyon Yerleştirme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="5cbf7-102">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="5cbf7-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5cbf7-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="5cbf7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5cbf7-105">Bu konu, özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IDockProvider>uygulamak için kılavuz ve kuralları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="5cbf7-106">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5cbf7-107"><xref:System.Windows.Automation.DockPattern> denetim stili, bir denetimin dock özelliklerini yerleştirme kapsayıcısı içinde göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-107">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="5cbf7-108">Bir yerleştirme kapsayıcısı, alt öğeleri yatay ve dikey olarak birbirlerine göre düzenlemenizi sağlayan bir denetimdir.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-108">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="5cbf7-109">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5cbf7-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="5cbf7-110">![İki sabitlenmiş alt öğe ile kapsayıcıyı sabitleme.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="5cbf7-110">![Docking container with two docked children.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="5cbf7-111">Visual Studio 'dan "Sınıf Görünümü" penceresinin DockPosition olduğu yere yerleştirme örneği. Right ve "Hata Listesi" Window, DockPosition. Bottom</span><span class="sxs-lookup"><span data-stu-id="5cbf7-111">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5cbf7-112">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="5cbf7-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5cbf7-113">Dock denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5cbf7-113">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="5cbf7-114"><xref:System.Windows.Automation.Provider.IDockProvider>, yerleştirme kapsayıcısının veya yerleştirme kapsayıcısı içindeki geçerli denetime bitişik yerleştirilmiş denetimlerin özelliklerinin herhangi bir özelliğini sunmaz.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-114"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
- <span data-ttu-id="5cbf7-115">Denetimler, geçerli z sıralarına göre birbirlerine göre sabitlenebilir; z sırası yerleşimi arttıkça, yerleştirme kapsayıcısının belirtilen kenarından de yerleştirilirler.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-115">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
- <span data-ttu-id="5cbf7-116">Yerleştirme kapsayıcısı yeniden boyutlandırılırsa, kapsayıcıdaki tüm yerleşik denetimler, özgün olarak yerleştirildikleri kenara yeniden konumlandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-116">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="5cbf7-117">Sabitlenmiş denetimler Ayrıca, <xref:System.Windows.Automation.DockPosition>yerleştirme davranışına göre kapsayıcının içindeki herhangi bir alanı dolduracak şekilde yeniden boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-117">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="5cbf7-118">Örneğin, <xref:System.Windows.Automation.DockPosition.Top> belirtilirse, denetimin sol ve sağ tarafları kullanılabilir alanı dolduracak şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-118">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="5cbf7-119"><xref:System.Windows.Automation.DockPosition.Fill> belirtilirse, denetimin dört kenarı kullanılabilir alanı dolduracak şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-119">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
- <span data-ttu-id="5cbf7-120">Birden çok Monitor sisteminde, denetimler geçerli izleyicinin sol veya sağ tarafına yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-120">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="5cbf7-121">Bu mümkün değilse, en soldaki izleyicinin sol tarafına veya en sağdaki monitörün sağ tarafına yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-121">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="5cbf7-122">IDockProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="5cbf7-122">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="5cbf7-123">IDockProvider arabirimini uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-123">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="5cbf7-124">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="5cbf7-124">Required members</span></span>|<span data-ttu-id="5cbf7-125">Üye türü</span><span class="sxs-lookup"><span data-stu-id="5cbf7-125">Member type</span></span>|<span data-ttu-id="5cbf7-126">Notlar</span><span class="sxs-lookup"><span data-stu-id="5cbf7-126">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="5cbf7-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="5cbf7-127">Property</span></span>|<span data-ttu-id="5cbf7-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="5cbf7-129">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5cbf7-129">Method</span></span>|<span data-ttu-id="5cbf7-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-130">None</span></span>|  
  
 <span data-ttu-id="5cbf7-131">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-131">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5cbf7-132">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="5cbf7-132">Exceptions</span></span>  
 <span data-ttu-id="5cbf7-133">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-133">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5cbf7-134">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="5cbf7-134">Exception type</span></span>|<span data-ttu-id="5cbf7-135">Koşul</span><span class="sxs-lookup"><span data-stu-id="5cbf7-135">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="5cbf7-136">-Bir denetim istenen yuva stilini yürütemediğinde.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-136">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5cbf7-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cbf7-137">See also</span></span>

- [<span data-ttu-id="5cbf7-138">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5cbf7-138">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="5cbf7-139">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="5cbf7-139">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="5cbf7-140">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="5cbf7-140">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="5cbf7-141">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5cbf7-141">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="5cbf7-142">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="5cbf7-142">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
