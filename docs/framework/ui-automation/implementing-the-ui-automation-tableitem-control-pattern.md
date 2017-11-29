---
title: "UI Otomasyon TableItem Denetim Düzeni Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5861ab24627f9b78cd20f97fcdb1b1b3d681991a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="c6036-102">UI Otomasyon TableItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="c6036-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="c6036-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="c6036-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c6036-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="c6036-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="c6036-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.ITableItemProvider>, olayları ve özellikleri hakkındaki bilgileri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="c6036-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="c6036-106">Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c6036-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="c6036-107"><xref:System.Windows.Automation.TableItemPattern> Denetim düzeni alt denetimler uygulamak kapsayıcıların desteklemek için kullanılan <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="c6036-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="c6036-108">Tek hücre işlevlere erişim gerekli eşzamanlı uygulaması tarafından sağlanan <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="c6036-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="c6036-109">Bu denetim düzeni paraleldir <xref:System.Windows.Automation.Provider.IGridItemProvider> herhangi bir uygulama denetim ayrım ile <xref:System.Windows.Automation.Provider.ITableItemProvider> tek hücre ve satır ve sütun bilgilerini arasındaki ilişkiyi program aracılığıyla kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6036-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="c6036-110">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="c6036-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="c6036-111">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="c6036-111">Implementation Guidelines and Conventions</span></span>  
  
-   <span data-ttu-id="c6036-112">İlgili kılavuz öğesi işlevsellik için bkz: [UI Otomasyon GridItem denetim düzeni uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c6036-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="c6036-113">Gerekli üyeleri ITableItemProvider için</span><span class="sxs-lookup"><span data-stu-id="c6036-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="c6036-114">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="c6036-114">Required member</span></span>|<span data-ttu-id="c6036-115">Üye türü</span><span class="sxs-lookup"><span data-stu-id="c6036-115">Member type</span></span>|<span data-ttu-id="c6036-116">Notlar</span><span class="sxs-lookup"><span data-stu-id="c6036-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="c6036-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c6036-117">Method</span></span>|<span data-ttu-id="c6036-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6036-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="c6036-119">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c6036-119">Method</span></span>|<span data-ttu-id="c6036-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6036-120">None</span></span>|  
  
 <span data-ttu-id="c6036-121">Bu denetim düzeni ilişkili özellikleri ya da olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="c6036-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="c6036-122">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="c6036-122">Exceptions</span></span>  
 <span data-ttu-id="c6036-123">Bu denetim düzeni ilişkili hiçbir özel durum vardır.</span><span class="sxs-lookup"><span data-stu-id="c6036-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6036-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6036-124">See Also</span></span>  
 [<span data-ttu-id="c6036-125">UI Otomasyon denetim düzenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="c6036-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="c6036-126">UI Otomasyon sağlayıcısında denetim düzenleri desteği</span><span class="sxs-lookup"><span data-stu-id="c6036-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="c6036-127">İstemciler için UI Otomasyon denetim düzenleri</span><span class="sxs-lookup"><span data-stu-id="c6036-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="c6036-128">UI Otomasyonu tablo denetim düzenini uygulama</span><span class="sxs-lookup"><span data-stu-id="c6036-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [<span data-ttu-id="c6036-129">UI Otomasyon GridItem denetim düzeni uygulama</span><span class="sxs-lookup"><span data-stu-id="c6036-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="c6036-130">UI Otomasyon ağacına genel bakış</span><span class="sxs-lookup"><span data-stu-id="c6036-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="c6036-131">UI otomasyonda önbelleğe almayı kullanma</span><span class="sxs-lookup"><span data-stu-id="c6036-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
