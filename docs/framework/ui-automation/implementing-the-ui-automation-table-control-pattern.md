---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 0b3d000112060550734890ad3c4063a26c320b04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180111"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="3be4e-102">UI Otomasyonu Tablo Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="3be4e-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="3be4e-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3be4e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3be4e-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3be4e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="3be4e-105">Bu konu, özellikler, yöntemler ve <xref:System.Windows.Automation.Provider.ITableProvider>olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları sunar.</span><span class="sxs-lookup"><span data-stu-id="3be4e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="3be4e-106">Ek başvurulara bağlantılar genel bakışın sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="3be4e-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="3be4e-107">Denetim <xref:System.Windows.Automation.TablePattern> deseni, alt öğelerin toplanması için kapsayıcı görevi yapan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3be4e-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="3be4e-108">Bu öğenin alt <xref:System.Windows.Automation.Provider.ITableItemProvider> uygulamak ve satır ve sütun tarafından geçilebilir iki boyutlu bir mantıksal koordinat sistemi içinde organize edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3be4e-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="3be4e-109">Bu denetim <xref:System.Windows.Automation.Provider.IGridProvider>deseni, herhangi bir denetim uygulamasının <xref:System.Windows.Automation.Provider.ITableProvider> her alt öğe için bir sütun ve/veya satır üstbilgi ilişkisini de ortaya koyması gerektiği ayrımıyla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="3be4e-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="3be4e-110">Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3be4e-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="3be4e-111">Uygulama Yönergeleri ve Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="3be4e-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="3be4e-112">Tablo denetim deseni uygulanırken aşağıdaki yönergeleri ve kuralları not edin:</span><span class="sxs-lookup"><span data-stu-id="3be4e-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="3be4e-113">Tek tek hücrelerin içeriğine erişim, gerekli eşzamanlı uygulama tarafından sağlanan iki boyutlu bir <xref:System.Windows.Automation.Provider.IGridProvider>mantıksal koordinat sistemi veya dizi üzerinden dir.</span><span class="sxs-lookup"><span data-stu-id="3be4e-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="3be4e-114">Sütun veya satır üstbilgi bir tablo nesnesi içinde bulunabilir veya bir tablo nesnesi ile ilişkili ayrı bir üstbilgi nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="3be4e-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="3be4e-115">Sütun ve satır üstbilgi, hem birincil üstbilgi hem de destekleyici üstbilgi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3be4e-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3be4e-116">Bu kavram, bir kullanıcının "Ad" sütunu tanımladığı Microsoft Excel elektronik tablosunda belirgin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="3be4e-116">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="3be4e-117">Bu sütunda artık iki üstbilgi vardır: kullanıcı tarafından tanımlanan "Ad" başlığı ve uygulama tarafından atanan bu sütuniçin alfasayısal atama.</span><span class="sxs-lookup"><span data-stu-id="3be4e-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="3be4e-118">İlgili ızgara işlevselliği için [UI Automation Grid Control Modelini uygulama](implementing-the-ui-automation-grid-control-pattern.md) hakkındabkz.</span><span class="sxs-lookup"><span data-stu-id="3be4e-118">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="3be4e-119">![Karmaşık üstbilgi öğeleri içeren tablo.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="3be4e-119">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="3be4e-120">Karmaşık Sütun Üstbilgili Tablo Örneği</span><span class="sxs-lookup"><span data-stu-id="3be4e-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="3be4e-121">![Belirsiz RowOrColumnMajor özelliğine sahip tablo.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="3be4e-121">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="3be4e-122">Belirsiz Satır Veya SütunAna Özelliği Olan Tablo Örneği</span><span class="sxs-lookup"><span data-stu-id="3be4e-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="3be4e-123">ITableProvider için Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="3be4e-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="3be4e-124">ITableProvider arabirimi için aşağıdaki özellikler ve yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3be4e-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="3be4e-125">Gerekli üyeler</span><span class="sxs-lookup"><span data-stu-id="3be4e-125">Required members</span></span>|<span data-ttu-id="3be4e-126">Üye tipi</span><span class="sxs-lookup"><span data-stu-id="3be4e-126">Member type</span></span>|<span data-ttu-id="3be4e-127">Notlar</span><span class="sxs-lookup"><span data-stu-id="3be4e-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="3be4e-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="3be4e-128">Property</span></span>|<span data-ttu-id="3be4e-129">None</span><span class="sxs-lookup"><span data-stu-id="3be4e-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="3be4e-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3be4e-130">Method</span></span>|<span data-ttu-id="3be4e-131">None</span><span class="sxs-lookup"><span data-stu-id="3be4e-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="3be4e-132">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3be4e-132">Method</span></span>|<span data-ttu-id="3be4e-133">None</span><span class="sxs-lookup"><span data-stu-id="3be4e-133">None</span></span>|  
  
 <span data-ttu-id="3be4e-134">Bu denetim deseni ilişkili olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="3be4e-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="3be4e-135">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="3be4e-135">Exceptions</span></span>  
 <span data-ttu-id="3be4e-136">Bu denetim deseni ilişkili özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="3be4e-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be4e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3be4e-137">See also</span></span>

- [<span data-ttu-id="3be4e-138">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3be4e-138">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="3be4e-139">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="3be4e-139">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="3be4e-140">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="3be4e-140">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="3be4e-141">UI Otomasyonu TableItem Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="3be4e-141">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="3be4e-142">UI Otomasyonu Grid Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="3be4e-142">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="3be4e-143">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3be4e-143">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="3be4e-144">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="3be4e-144">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
