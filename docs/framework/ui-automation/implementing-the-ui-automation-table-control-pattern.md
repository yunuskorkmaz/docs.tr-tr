---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
description: UI Otomasyonu 'nda tablo Denetim modelini uygulamak için yönergeleri ve kuralları gözden geçirin. ITableProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: e88ddee04ba887daf1929d855526cd0d062f78d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168245"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="4fa60-104">UI Otomasyonu Tablo Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="4fa60-104">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="4fa60-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="4fa60-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4fa60-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="4fa60-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="4fa60-107">Bu konuda <xref:System.Windows.Automation.Provider.ITableProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fa60-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="4fa60-108">Ek başvuruların bağlantıları genel bakış sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="4fa60-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="4fa60-109"><xref:System.Windows.Automation.TablePattern>Denetim stili, alt öğelerin bir koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4fa60-109">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="4fa60-110">Bu öğenin alt öğeleri, <xref:System.Windows.Automation.Provider.ITableItemProvider> satır ve sütun tarafından geçilen iki boyutlu bir mantıksal koordinat sisteminde uygulamanız ve düzenlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4fa60-110">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="4fa60-111">Bu denetim deseninin <xref:System.Windows.Automation.Provider.IGridProvider> , <xref:System.Windows.Automation.Provider.ITableProvider> her bir alt öğe için aynı zamanda bir sütun ve/veya satır üst bilgisi ilişkisi olması gereken ayrım ile benzerdir.</span><span class="sxs-lookup"><span data-stu-id="4fa60-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="4fa60-112">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="4fa60-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="4fa60-113">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="4fa60-113">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="4fa60-114">Tablo denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4fa60-114">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="4fa60-115">Tek tek hücrelerin içeriğine erişim, iki boyutlu bir mantıksal koordinat sistemi veya ' nin gerekli eşzamanlı uygulamasıyla belirtilen dizisidir <xref:System.Windows.Automation.Provider.IGridProvider> .</span><span class="sxs-lookup"><span data-stu-id="4fa60-115">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="4fa60-116">Bir sütun veya satır üst bilgisi, tablo nesnesi içinde veya tablo nesnesiyle ilişkili ayrı bir üst bilgi nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa60-116">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="4fa60-117">Sütun ve satır başlıkları hem birincil üstbilgiyi hem de tüm destekleyici üst bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa60-117">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fa60-118">Bu kavram, bir kullanıcının "Ilk ad" sütunu tanımladığı bir Microsoft Excel elektronik tablosunda görünür hale gelir.</span><span class="sxs-lookup"><span data-stu-id="4fa60-118">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="4fa60-119">Bu sütunda artık iki üst bilgi vardır: Kullanıcı tarafından tanımlanan "Ilk ad" üstbilgisi ve uygulama tarafından atanan sütun için alfasayısal atama.</span><span class="sxs-lookup"><span data-stu-id="4fa60-119">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="4fa60-120">İlgili kılavuz işlevselliği için [UI Otomasyonu kılavuz denetim modelini uygulama](implementing-the-ui-automation-grid-control-pattern.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4fa60-120">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="4fa60-121">![Karmaşık üstbilgi öğeleri içeren tablo.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="4fa60-121">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="4fa60-122">Karmaşık sütun başlıkları içeren bir tablo örneği</span><span class="sxs-lookup"><span data-stu-id="4fa60-122">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="4fa60-123">![Belirsiz Roworcolumnana özelliği olan tablo.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="4fa60-123">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="4fa60-124">Belirsiz Roworcolumnana özelliği olan bir tablo örneği</span><span class="sxs-lookup"><span data-stu-id="4fa60-124">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="4fa60-125">ITableProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="4fa60-125">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="4fa60-126">ITableProvider arabirimi için aşağıdaki özellikler ve Yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4fa60-126">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="4fa60-127">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="4fa60-127">Required members</span></span>|<span data-ttu-id="4fa60-128">Üye türü</span><span class="sxs-lookup"><span data-stu-id="4fa60-128">Member type</span></span>|<span data-ttu-id="4fa60-129">Notlar</span><span class="sxs-lookup"><span data-stu-id="4fa60-129">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="4fa60-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="4fa60-130">Property</span></span>|<span data-ttu-id="4fa60-131">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="4fa60-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="4fa60-132">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4fa60-132">Method</span></span>|<span data-ttu-id="4fa60-133">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="4fa60-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="4fa60-134">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4fa60-134">Method</span></span>|<span data-ttu-id="4fa60-135">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="4fa60-135">None</span></span>|  
  
 <span data-ttu-id="4fa60-136">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="4fa60-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="4fa60-137">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="4fa60-137">Exceptions</span></span>  
 <span data-ttu-id="4fa60-138">Bu denetim deseninin ilişkili özel durumları yok.</span><span class="sxs-lookup"><span data-stu-id="4fa60-138">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa60-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fa60-139">See also</span></span>

- [<span data-ttu-id="4fa60-140">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4fa60-140">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="4fa60-141">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="4fa60-141">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="4fa60-142">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="4fa60-142">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="4fa60-143">UI Otomasyon TableItem Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="4fa60-143">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="4fa60-144">UI Otomasyon Kılavuz Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="4fa60-144">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="4fa60-145">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4fa60-145">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="4fa60-146">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="4fa60-146">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
