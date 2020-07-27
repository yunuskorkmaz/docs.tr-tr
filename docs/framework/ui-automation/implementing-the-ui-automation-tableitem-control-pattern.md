---
title: UI Otomasyon TableItem Denetim Düzeni Uygulama
description: UI Otomasyonu 'nda TableItem denetim modelini uygulamak için yönergeleri ve kuralları gözden geçirin. ITableItemProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: 3d6d31fe0e041fbba147df14d290a775188755f2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163518"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="deb92-104">UI Otomasyon TableItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="deb92-104">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="deb92-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="deb92-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="deb92-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="deb92-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="deb92-107">Bu konu <xref:System.Windows.Automation.Provider.ITableItemProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="deb92-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="deb92-108">Ek başvuruların bağlantıları genel bakış sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="deb92-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="deb92-109"><xref:System.Windows.Automation.TableItemPattern>Denetim stili, uygulayan kapsayıcıların alt denetimlerini desteklemek için kullanılır <xref:System.Windows.Automation.Provider.ITableProvider> .</span><span class="sxs-lookup"><span data-stu-id="deb92-109">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="deb92-110">Bağımsız hücre işlevselliğine erişim, için gerekli olan eşzamanlı uygulamayla sağlanır <xref:System.Windows.Automation.Provider.IGridItemProvider> .</span><span class="sxs-lookup"><span data-stu-id="deb92-110">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="deb92-111">Bu denetim deseninin, <xref:System.Windows.Automation.Provider.IGridItemProvider> uygulayan herhangi bir denetimin, tek bir hücre ve <xref:System.Windows.Automation.Provider.ITableItemProvider> onun satırı ve sütun bilgileri arasındaki ilişkiyi programlı bir şekilde kullanıma sunmasının gereken ayrım ile benzerdir.</span><span class="sxs-lookup"><span data-stu-id="deb92-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="deb92-112">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="deb92-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="deb92-113">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="deb92-113">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="deb92-114">İlgili ızgara öğesi işlevselliği için bkz. [UI Otomasyonu GridItem denetim modelini uygulama](implementing-the-ui-automation-griditem-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="deb92-114">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="deb92-115">ITableItemProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="deb92-115">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="deb92-116">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="deb92-116">Required member</span></span>|<span data-ttu-id="deb92-117">Üye türü</span><span class="sxs-lookup"><span data-stu-id="deb92-117">Member type</span></span>|<span data-ttu-id="deb92-118">Notlar</span><span class="sxs-lookup"><span data-stu-id="deb92-118">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="deb92-119">Yöntem</span><span class="sxs-lookup"><span data-stu-id="deb92-119">Method</span></span>|<span data-ttu-id="deb92-120">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="deb92-120">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="deb92-121">Yöntem</span><span class="sxs-lookup"><span data-stu-id="deb92-121">Method</span></span>|<span data-ttu-id="deb92-122">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="deb92-122">None</span></span>|  
  
 <span data-ttu-id="deb92-123">Bu denetim deseninin ilişkili özellikleri veya olayları yok.</span><span class="sxs-lookup"><span data-stu-id="deb92-123">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="deb92-124">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="deb92-124">Exceptions</span></span>  
 <span data-ttu-id="deb92-125">Bu denetim deseninin ilişkili özel durumları yok.</span><span class="sxs-lookup"><span data-stu-id="deb92-125">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb92-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deb92-126">See also</span></span>

- [<span data-ttu-id="deb92-127">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="deb92-127">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="deb92-128">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="deb92-128">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="deb92-129">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="deb92-129">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="deb92-130">UI Otomasyonu Tablo Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="deb92-130">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="deb92-131">UI Otomasyon GridItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="deb92-131">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="deb92-132">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="deb92-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="deb92-133">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="deb92-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
