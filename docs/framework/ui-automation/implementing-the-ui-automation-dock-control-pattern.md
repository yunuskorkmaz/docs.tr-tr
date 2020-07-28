---
title: UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
description: UI Otomasyon Dock denetim modelini uygulamayı öğrenin. Bir denetimin dock özelliklerini göstermek için Dockmodel denetim modelini kullanın. IDockProvider 'ı uygulayın.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
ms.openlocfilehash: 8080d78c7bded3cb884f92948eb1259cda5544dc
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165898"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="89bf8-105">UI Otomasyon Yerleştirme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="89bf8-105">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="89bf8-106">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="89bf8-106">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="89bf8-107">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="89bf8-107">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="89bf8-108">Bu konu <xref:System.Windows.Automation.Provider.IDockProvider> , özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="89bf8-108">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="89bf8-109">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="89bf8-109">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="89bf8-110"><xref:System.Windows.Automation.DockPattern>Denetim deseninin, bir yerleştirme kapsayıcısı içindeki denetimin dock özelliklerini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="89bf8-110">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="89bf8-111">Bir yerleştirme kapsayıcısı, alt öğeleri yatay ve dikey olarak birbirlerine göre düzenlemenizi sağlayan bir denetimdir.</span><span class="sxs-lookup"><span data-stu-id="89bf8-111">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="89bf8-112">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="89bf8-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="89bf8-113">![İki sabitlenmiş alt öğe ile kapsayıcıyı sabitleme.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="89bf8-113">![Docking container with two docked children.](./media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="89bf8-114">Visual Studio 'dan "Sınıf Görünümü" penceresinin DockPosition olduğu yere yerleştirme örneği. Right ve "Hata Listesi" Window, DockPosition. Bottom</span><span class="sxs-lookup"><span data-stu-id="89bf8-114">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="89bf8-115">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="89bf8-115">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="89bf8-116">Dock denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="89bf8-116">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="89bf8-117"><xref:System.Windows.Automation.Provider.IDockProvider>, yerleştirme kapsayıcısının veya yerleştirme kapsayıcısı içindeki geçerli denetime bitişik yerleştirilmiş denetimlerin özelliklerinin herhangi bir özelliğini açığa çıkarmaz.</span><span class="sxs-lookup"><span data-stu-id="89bf8-117"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
- <span data-ttu-id="89bf8-118">Denetimler, geçerli z sıralarına göre birbirlerine göre sabitlenebilir; z sırası yerleşimi arttıkça, yerleştirme kapsayıcısının belirtilen kenarından de yerleştirilirler.</span><span class="sxs-lookup"><span data-stu-id="89bf8-118">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
- <span data-ttu-id="89bf8-119">Yerleştirme kapsayıcısı yeniden boyutlandırılırsa, kapsayıcıdaki tüm yerleşik denetimler, özgün olarak yerleştirildikleri kenara yeniden konumlandırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="89bf8-119">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="89bf8-120">Sabitlenmiş denetimler Ayrıca, kapsayıcının içindeki herhangi bir alanı kendi yerleştirme davranışına göre dolduracak şekilde yeniden boyutlandırılır <xref:System.Windows.Automation.DockPosition> .</span><span class="sxs-lookup"><span data-stu-id="89bf8-120">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="89bf8-121">Örneğin, belirtilirse, <xref:System.Windows.Automation.DockPosition.Top> denetimin sol ve sağ kenarları, kullanılabilir alanı dolduracak şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="89bf8-121">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="89bf8-122"><xref:System.Windows.Automation.DockPosition.Fill>Belirtilmişse, denetimin dört kenarı kullanılabilir alanı dolduracak şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="89bf8-122">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
- <span data-ttu-id="89bf8-123">Birden çok Monitor sisteminde, denetimler geçerli izleyicinin sol veya sağ tarafına yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="89bf8-123">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="89bf8-124">Bu mümkün değilse, en soldaki izleyicinin sol tarafına veya en sağdaki monitörün sağ tarafına yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="89bf8-124">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="89bf8-125">IDockProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="89bf8-125">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="89bf8-126">IDockProvider arabirimini uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="89bf8-126">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="89bf8-127">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="89bf8-127">Required members</span></span>|<span data-ttu-id="89bf8-128">Üye türü</span><span class="sxs-lookup"><span data-stu-id="89bf8-128">Member type</span></span>|<span data-ttu-id="89bf8-129">Notlar</span><span class="sxs-lookup"><span data-stu-id="89bf8-129">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="89bf8-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="89bf8-130">Property</span></span>|<span data-ttu-id="89bf8-131">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="89bf8-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="89bf8-132">Yöntem</span><span class="sxs-lookup"><span data-stu-id="89bf8-132">Method</span></span>|<span data-ttu-id="89bf8-133">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="89bf8-133">None</span></span>|  
  
 <span data-ttu-id="89bf8-134">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="89bf8-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="89bf8-135">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="89bf8-135">Exceptions</span></span>  
 <span data-ttu-id="89bf8-136">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="89bf8-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="89bf8-137">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="89bf8-137">Exception type</span></span>|<span data-ttu-id="89bf8-138">Koşul</span><span class="sxs-lookup"><span data-stu-id="89bf8-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="89bf8-139">-Bir denetim istenen yuva stilini yürütemediğinde.</span><span class="sxs-lookup"><span data-stu-id="89bf8-139">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89bf8-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89bf8-140">See also</span></span>

- [<span data-ttu-id="89bf8-141">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="89bf8-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="89bf8-142">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="89bf8-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="89bf8-143">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="89bf8-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="89bf8-144">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="89bf8-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="89bf8-145">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="89bf8-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
