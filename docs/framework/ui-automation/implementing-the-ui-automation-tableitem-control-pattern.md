---
title: UI Otomasyon TableItem Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: f35b491c31e8725eac0025dfd6815079d0ea9b79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180071"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="deefc-102">UI Otomasyon TableItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="deefc-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="deefc-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="deefc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="deefc-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="deefc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="deefc-105">Bu <xref:System.Windows.Automation.Provider.ITableItemProvider>konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere, uygulama yönergeleri ve kuralları sunar.</span><span class="sxs-lookup"><span data-stu-id="deefc-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="deefc-106">Ek başvurulara bağlantılar genel bakışın sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="deefc-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="deefc-107">Denetim <xref:System.Windows.Automation.TableItemPattern> deseni, uygulayan <xref:System.Windows.Automation.Provider.ITableProvider>kapsayıcıların alt denetimlerini desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="deefc-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="deefc-108">Tek tek hücre işlevselliği erişim gerekli eşzamanlı <xref:System.Windows.Automation.Provider.IGridItemProvider>uygulama tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="deefc-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="deefc-109">Bu denetim deseni, <xref:System.Windows.Automation.Provider.IGridItemProvider> herhangi bir denetim uygulamasının tek tek hücre ile satır ve sütun bilgileri arasındaki ilişkiyi programlı olarak ortaya koyması <xref:System.Windows.Automation.Provider.ITableItemProvider> gerektiği ayrımına benzer.</span><span class="sxs-lookup"><span data-stu-id="deefc-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="deefc-110">Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="deefc-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="deefc-111">Uygulama Yönergeleri ve Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="deefc-111">Implementation Guidelines and Conventions</span></span>  
  
- <span data-ttu-id="deefc-112">İlgili ızgara öğesi işlevselliği için [bkz.](implementing-the-ui-automation-griditem-control-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="deefc-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="deefc-113">ITableItemProvider için Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="deefc-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="deefc-114">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="deefc-114">Required member</span></span>|<span data-ttu-id="deefc-115">Üye tipi</span><span class="sxs-lookup"><span data-stu-id="deefc-115">Member type</span></span>|<span data-ttu-id="deefc-116">Notlar</span><span class="sxs-lookup"><span data-stu-id="deefc-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="deefc-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="deefc-117">Method</span></span>|<span data-ttu-id="deefc-118">None</span><span class="sxs-lookup"><span data-stu-id="deefc-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="deefc-119">Yöntem</span><span class="sxs-lookup"><span data-stu-id="deefc-119">Method</span></span>|<span data-ttu-id="deefc-120">None</span><span class="sxs-lookup"><span data-stu-id="deefc-120">None</span></span>|  
  
 <span data-ttu-id="deefc-121">Bu denetim deseni ilişkili özellikleri veya olayları vardır.</span><span class="sxs-lookup"><span data-stu-id="deefc-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="deefc-122">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="deefc-122">Exceptions</span></span>  
 <span data-ttu-id="deefc-123">Bu denetim deseni ilişkili özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="deefc-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deefc-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deefc-124">See also</span></span>

- [<span data-ttu-id="deefc-125">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="deefc-125">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="deefc-126">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="deefc-126">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="deefc-127">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="deefc-127">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="deefc-128">UI Otomasyonu Table Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="deefc-128">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="deefc-129">UI Otomasyonu GridItem Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="deefc-129">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="deefc-130">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="deefc-130">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="deefc-131">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="deefc-131">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
