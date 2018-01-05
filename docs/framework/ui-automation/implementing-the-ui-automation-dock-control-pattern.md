---
title: "UI Otomasyon Yerleştirme Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 136d4ec56cf0c78aac03d1b3f44a18cd268d3bc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="5646c-102">UI Otomasyon Yerleştirme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="5646c-102">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="5646c-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5646c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5646c-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5646c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5646c-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IDockProvider>, özellikler hakkında bilgiler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="5646c-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="5646c-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5646c-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="5646c-107"><xref:System.Windows.Automation.DockPattern> Denetim düzeni takma kapsayıcı içindeki bir denetim yerleştirme özelliklerini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5646c-107">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="5646c-108">Alt öğelerini yatay ve dikey olarak, diğer göre düzenlemek izin veren bir denetim bir takma kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="5646c-108">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="5646c-109">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="5646c-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="5646c-110">![Kapsayıcı yerleştirilmiş iki alt öğeyle yerleştirme. ] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="5646c-110">![Docking container with two docked children.](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="5646c-111">DockPosition.Bottom olan "Sınıf Görünümü" penceresi DockPosition.Right ve "Hata listesi" penceresini olduğu örnek Visual Studio'dan yerleştirme</span><span class="sxs-lookup"><span data-stu-id="5646c-111">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="5646c-112">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="5646c-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="5646c-113">Yerleştirme denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="5646c-113">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="5646c-114"><xref:System.Windows.Automation.Provider.IDockProvider>yerleştirme kapsayıcının herhangi bir özellik veya takma kapsayıcı içindeki geçerli denetim bitişik yerleştirilmiş denetimlerinin herhangi bir özellik kullanıma sunmuyor.</span><span class="sxs-lookup"><span data-stu-id="5646c-114"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
-   <span data-ttu-id="5646c-115">Denetimleri birbirine geçerli kendi z-sırasına göre yerleştirilmiş; en yüksek takma kapsayıcı belirtilen kenarından yerleştirilen bunlar z düzeni yatırımlarından, uzağa.</span><span class="sxs-lookup"><span data-stu-id="5646c-115">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
-   <span data-ttu-id="5646c-116">Yerleştirme kapsayıcı boyutlandırılır, kapsayıcı içindeki herhangi bir yerleşik Denetim temizleme için bunlar ilk olarak yerleşik kenarına konumlandırılmasına.</span><span class="sxs-lookup"><span data-stu-id="5646c-116">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="5646c-117">Yerleşik denetimleri de yerleştirme davranışını göre kapsayıcı içindeki herhangi bir alanı dolduracak şekilde yeniden boyutlandırılır kendi <xref:System.Windows.Automation.DockPosition>.</span><span class="sxs-lookup"><span data-stu-id="5646c-117">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="5646c-118">Örneğin, varsa <xref:System.Windows.Automation.DockPosition.Top> belirtilirse, sol ve sağ tarafa denetiminin tüm kullanılabilir alanı dolduracak şekilde genişletin.</span><span class="sxs-lookup"><span data-stu-id="5646c-118">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="5646c-119">Varsa <xref:System.Windows.Automation.DockPosition.Fill> belirtilmemişse, denetimi dört tarafına tüm kullanılabilir alanı dolduracak şekilde genişletin.</span><span class="sxs-lookup"><span data-stu-id="5646c-119">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
-   <span data-ttu-id="5646c-120">Birden çok monitör sistemde sol veya sağ tarafındaki geçerli izleme denetimleri yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="5646c-120">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="5646c-121">Bu mümkün değilse, soldaki monitörün sol tarafındaki veya en sağdaki monitöre sağ tarafındaki yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="5646c-121">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="5646c-122">Gerekli üyeleri IDockProvider için</span><span class="sxs-lookup"><span data-stu-id="5646c-122">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="5646c-123">Aşağıdaki özellikleri ve yöntemleri IDockProvider arabirimi uygulamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5646c-123">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="5646c-124">Gerekli üyeleri</span><span class="sxs-lookup"><span data-stu-id="5646c-124">Required members</span></span>|<span data-ttu-id="5646c-125">Üye türü</span><span class="sxs-lookup"><span data-stu-id="5646c-125">Member type</span></span>|<span data-ttu-id="5646c-126">Notlar</span><span class="sxs-lookup"><span data-stu-id="5646c-126">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="5646c-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="5646c-127">Property</span></span>|<span data-ttu-id="5646c-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="5646c-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="5646c-129">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5646c-129">Method</span></span>|<span data-ttu-id="5646c-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="5646c-130">None</span></span>|  
  
 <span data-ttu-id="5646c-131">Bu denetim düzeni ilişkili olay vardır.</span><span class="sxs-lookup"><span data-stu-id="5646c-131">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="5646c-132">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="5646c-132">Exceptions</span></span>  
 <span data-ttu-id="5646c-133">Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.</span><span class="sxs-lookup"><span data-stu-id="5646c-133">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="5646c-134">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="5646c-134">Exception type</span></span>|<span data-ttu-id="5646c-135">Koşul</span><span class="sxs-lookup"><span data-stu-id="5646c-135">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="5646c-136">-Ne zaman bir denetim istenen yerleştirme stilini yürütme mümkün değil.</span><span class="sxs-lookup"><span data-stu-id="5646c-136">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5646c-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5646c-137">See Also</span></span>  
 [<span data-ttu-id="5646c-138">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5646c-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="5646c-139">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="5646c-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="5646c-140">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="5646c-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="5646c-141">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5646c-141">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="5646c-142">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="5646c-142">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
