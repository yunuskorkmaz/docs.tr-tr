---
title: UI Otomasyon TableItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 3893f69ca6f73665ea3ea4b4f07970b847097f11
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649463"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="78ffa-102">UI Otomasyon TableItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="78ffa-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="78ffa-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="78ffa-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="78ffa-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="78ffa-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="78ffa-105">Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.ITableItemProvider>, olayları ve özellikleri hakkında bilgi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="78ffa-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="78ffa-106">Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="78ffa-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="78ffa-107"><xref:System.Windows.Automation.TableItemPattern> Denetim düzeni uygulama kapsayıcılarının alt denetimler desteklemek için kullanılan <xref:System.Windows.Automation.Provider.ITableProvider>.</span><span class="sxs-lookup"><span data-stu-id="78ffa-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="78ffa-108">Tek hücre işlevlerine erişmek için gerekli eşzamanlı uygulaması tarafından sağlanan <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span><span class="sxs-lookup"><span data-stu-id="78ffa-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="78ffa-109">Bu denetim düzeni benzer <xref:System.Windows.Automation.Provider.IGridItemProvider> ile tüm uygulama denetim ayrım <xref:System.Windows.Automation.Provider.ITableItemProvider> program aracılığıyla tek bir hücre, satır ve sütun bilgisi arasındaki ilişkiyi kullanıma sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="78ffa-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="78ffa-110">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="78ffa-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="78ffa-111">Uygulama yönergeleri ve kuralları</span><span class="sxs-lookup"><span data-stu-id="78ffa-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="78ffa-112">Görmek için ilgili kılavuz öğesi işlevsellik, [UI Otomasyon GridItem denetim desenini uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="78ffa-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="78ffa-113">Gerekli üyeleri ITableItemProvider için</span><span class="sxs-lookup"><span data-stu-id="78ffa-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="78ffa-114">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="78ffa-114">Required member</span></span>|<span data-ttu-id="78ffa-115">Üye türü</span><span class="sxs-lookup"><span data-stu-id="78ffa-115">Member type</span></span>|<span data-ttu-id="78ffa-116">Notlar</span><span class="sxs-lookup"><span data-stu-id="78ffa-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="78ffa-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="78ffa-117">Method</span></span>|<span data-ttu-id="78ffa-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="78ffa-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="78ffa-119">Yöntem</span><span class="sxs-lookup"><span data-stu-id="78ffa-119">Method</span></span>|<span data-ttu-id="78ffa-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="78ffa-120">None</span></span>|  
  
 <span data-ttu-id="78ffa-121">Bu denetim düzeni hiçbir ilişkili özellikleri veya olayları vardır.</span><span class="sxs-lookup"><span data-stu-id="78ffa-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="78ffa-122">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="78ffa-122">Exceptions</span></span>  
 <span data-ttu-id="78ffa-123">Bu denetim düzeni ilişkili hiçbir özel durum vardır.</span><span class="sxs-lookup"><span data-stu-id="78ffa-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ffa-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78ffa-124">See also</span></span>

- [<span data-ttu-id="78ffa-125">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="78ffa-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="78ffa-126">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="78ffa-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="78ffa-127">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="78ffa-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="78ffa-128">UI Otomasyonu Table Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="78ffa-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="78ffa-129">UI Otomasyonu GridItem Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="78ffa-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="78ffa-130">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="78ffa-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="78ffa-131">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="78ffa-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
