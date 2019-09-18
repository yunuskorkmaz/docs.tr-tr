---
title: UI Otomasyon TableItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: cdbfc8d24dce3b63801682528a49c13d89660935
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043170"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="fdedc-102">UI Otomasyon TableItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="fdedc-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="fdedc-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="fdedc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fdedc-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="fdedc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="fdedc-105">Bu konu, olaylar ve özellikler hakkında bilgiler <xref:System.Windows.Automation.Provider.ITableItemProvider>de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="fdedc-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="fdedc-106">Ek başvuruların bağlantıları genel bakış sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="fdedc-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="fdedc-107">Denetim stili, uygulayan <xref:System.Windows.Automation.Provider.ITableProvider>kapsayıcıların alt denetimlerini desteklemek için kullanılır. <xref:System.Windows.Automation.TableItemPattern></span><span class="sxs-lookup"><span data-stu-id="fdedc-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="fdedc-108">Bağımsız hücre işlevselliğine erişim, için gerekli olan <xref:System.Windows.Automation.Provider.IGridItemProvider>eşzamanlı uygulamayla sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fdedc-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="fdedc-109">Bu denetim deseninin, uygulayan <xref:System.Windows.Automation.Provider.IGridItemProvider> <xref:System.Windows.Automation.Provider.ITableItemProvider> herhangi bir denetimin, tek bir hücre ve onun satırı ve sütun bilgileri arasındaki ilişkiyi programlı bir şekilde kullanıma sunmasının gereken ayrım ile benzerdir.</span><span class="sxs-lookup"><span data-stu-id="fdedc-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="fdedc-110">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="fdedc-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="fdedc-111">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="fdedc-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="fdedc-112">İlgili ızgara öğesi işlevselliği için bkz. [UI Otomasyonu GridItem denetim modelini uygulama](implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="fdedc-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="fdedc-113">ITableItemProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="fdedc-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="fdedc-114">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="fdedc-114">Required member</span></span>|<span data-ttu-id="fdedc-115">Üye türü</span><span class="sxs-lookup"><span data-stu-id="fdedc-115">Member type</span></span>|<span data-ttu-id="fdedc-116">Notlar</span><span class="sxs-lookup"><span data-stu-id="fdedc-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="fdedc-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fdedc-117">Method</span></span>|<span data-ttu-id="fdedc-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="fdedc-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="fdedc-119">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fdedc-119">Method</span></span>|<span data-ttu-id="fdedc-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="fdedc-120">None</span></span>|  
  
 <span data-ttu-id="fdedc-121">Bu denetim deseninin ilişkili özellikleri veya olayları yok.</span><span class="sxs-lookup"><span data-stu-id="fdedc-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="fdedc-122">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="fdedc-122">Exceptions</span></span>  
 <span data-ttu-id="fdedc-123">Bu denetim deseninin ilişkili özel durumları yok.</span><span class="sxs-lookup"><span data-stu-id="fdedc-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdedc-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdedc-124">See also</span></span>

- [<span data-ttu-id="fdedc-125">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fdedc-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="fdedc-126">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="fdedc-126">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="fdedc-127">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="fdedc-127">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="fdedc-128">UI Otomasyonu Table Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="fdedc-128">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="fdedc-129">UI Otomasyonu GridItem Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="fdedc-129">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="fdedc-130">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fdedc-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="fdedc-131">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="fdedc-131">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
