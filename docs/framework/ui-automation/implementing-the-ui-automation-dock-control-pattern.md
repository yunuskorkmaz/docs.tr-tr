---
title: UI Otomasyon Yerleştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 875a9f3a20b7bb5e66ecf3f6b5e3b3cf229e2bf9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659815"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="8c0b6-102">UI Otomasyon Yerleştirme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="8c0b6-102">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="8c0b6-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8c0b6-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8c0b6-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8c0b6-105">Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IDockProvider>, özellikler hakkında bilgiler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="8c0b6-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="8c0b6-107"><xref:System.Windows.Automation.DockPattern> Denetim düzeni yerleştirme bir kapsayıcıdaki bir denetim noktası özelliklerini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-107">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="8c0b6-108">Alt öğeleri Yatayda ve Dikeyde, birbirine göre düzenlemek izin veren bir denetimi bir yerleştirme kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-108">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="8c0b6-109">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8c0b6-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="8c0b6-110">![İki yerleşik alt ile kapsayıcı yerleştirme. ](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="8c0b6-110">![Docking container with two docked children.](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="8c0b6-111">Visual Studio'dan örnek "Class View" penceresinde DockPosition.Right ve "Hata listesi" penceresinde olduğu yerleştirme DockPosition.Bottom olduğu</span><span class="sxs-lookup"><span data-stu-id="8c0b6-111">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8c0b6-112">Uygulama yönergeleri ve kuralları</span><span class="sxs-lookup"><span data-stu-id="8c0b6-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8c0b6-113">Dock denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="8c0b6-113">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="8c0b6-114"><xref:System.Windows.Automation.Provider.IDockProvider> yerleştirme kapsayıcının herhangi bir özelliği ya da yerleştirme kapsayıcıdaki geçerli denetim bitişik yerleştirilen denetimlerin herhangi bir özelliği kullanıma sunmuyor.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-114"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
-   <span data-ttu-id="8c0b6-115">Denetimleri birbirine geçerli kendi z-düzeni tabanlı yerleştirilmiştir; en yüksek yerleştirme kapsayıcının belirtilen edge'den yerleştirilen, z düzenini yatırımlarından, daha da esnetmenize.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-115">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
-   <span data-ttu-id="8c0b6-116">Yerleştirme kapsayıcı boyutlandırılırsa, kapsayıcı içindeki herhangi bir yerleşik denetim, bunlar ilk olarak yerleştirildi kenarına temizleme konumlandırılmasına.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-116">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="8c0b6-117">Yerleşik denetimler de yerleştirme davranışını göre kapsayıcıdaki herhangi bir alanı doldurmak için boyutlandırılır kendi <xref:System.Windows.Automation.DockPosition>.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-117">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="8c0b6-118">Örneğin, varsa <xref:System.Windows.Automation.DockPosition.Top> belirtilir ve denetimin sol tarafında tüm kullanılabilir alanı dolduracak şekilde genişletin.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-118">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="8c0b6-119">Varsa <xref:System.Windows.Automation.DockPosition.Fill> belirtilirse, denetimin dört tarafına tüm kullanılabilir alanı dolduracak şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-119">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
-   <span data-ttu-id="8c0b6-120">Bir çoklu monitör sisteminde sol veya sağ tarafında geçerli izleyici denetimleri yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-120">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="8c0b6-121">Bu mümkün değilse, en soldaki monitöre sol tarafındaki veya sağdaki ekranın sağ tarafındaki dock.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-121">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="8c0b6-122">Gerekli üyeleri IDockProvider için</span><span class="sxs-lookup"><span data-stu-id="8c0b6-122">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="8c0b6-123">Aşağıdaki özellikleri ve yöntemleri IDockProvider arabirim uygulamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-123">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="8c0b6-124">Gerekli üyeleri</span><span class="sxs-lookup"><span data-stu-id="8c0b6-124">Required members</span></span>|<span data-ttu-id="8c0b6-125">Üye türü</span><span class="sxs-lookup"><span data-stu-id="8c0b6-125">Member type</span></span>|<span data-ttu-id="8c0b6-126">Notlar</span><span class="sxs-lookup"><span data-stu-id="8c0b6-126">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="8c0b6-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="8c0b6-127">Property</span></span>|<span data-ttu-id="8c0b6-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="8c0b6-129">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8c0b6-129">Method</span></span>|<span data-ttu-id="8c0b6-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-130">None</span></span>|  
  
 <span data-ttu-id="8c0b6-131">Bu denetim düzeni, ilişkili olay vardır.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-131">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="8c0b6-132">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="8c0b6-132">Exceptions</span></span>  
 <span data-ttu-id="8c0b6-133">Sağlayıcıları, aşağıdaki özel durumlar gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-133">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="8c0b6-134">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="8c0b6-134">Exception type</span></span>|<span data-ttu-id="8c0b6-135">Koşul</span><span class="sxs-lookup"><span data-stu-id="8c0b6-135">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="8c0b6-136">-Bir denetimi istenen dock stili yürütebilmek için değil.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-136">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c0b6-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c0b6-137">See Also</span></span>  
 [<span data-ttu-id="8c0b6-138">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8c0b6-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="8c0b6-139">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="8c0b6-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="8c0b6-140">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="8c0b6-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="8c0b6-141">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8c0b6-141">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="8c0b6-142">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="8c0b6-142">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
