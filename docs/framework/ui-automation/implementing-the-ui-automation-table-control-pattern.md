---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 955d9f005a45ab805012dd43cbef27877a9dfdb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398586"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="b6ddf-102">UI Otomasyonu Tablo Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="b6ddf-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="b6ddf-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b6ddf-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="b6ddf-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b6ddf-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.ITableProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="b6ddf-106">Ek başvurular bağlantılar genel bakış sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="b6ddf-107"><xref:System.Windows.Automation.TablePattern> Denetim düzeni alt öğe koleksiyonunu için kapsayıcı olarak hareket denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="b6ddf-108">Bu öğenin alt öğeleri uygulamalıdır <xref:System.Windows.Automation.Provider.ITableItemProvider> ve satır ve sütun tarafından geçiş bir iki boyutlu mantıksal koordinat sistemi düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="b6ddf-109">Bu denetim düzeni paraleldir <xref:System.Windows.Automation.Provider.IGridProvider>, herhangi bir uygulama denetim ayrım ile <xref:System.Windows.Automation.Provider.ITableProvider> her alt öğesi için bir sütun ve/veya satır üstbilgisi ilişki de kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="b6ddf-110">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b6ddf-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b6ddf-111">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="b6ddf-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="b6ddf-112">Tablo denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="b6ddf-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="b6ddf-113">Tek tek hücreler içeriğe erişimi olan bir iki boyutlu mantıksal koordinat sistemi ya da gerekli eşzamanlı uygulaması tarafından sağlanan dizi yoluyla <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
-   <span data-ttu-id="b6ddf-114">Bir sütun veya satır üstbilgisi bir tablo nesnesi içinde bulunabilir veya bir tablo nesneyle ilişkilendirilen bir ayrı bir üstbilgi nesnesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
-   <span data-ttu-id="b6ddf-115">Sütun ve satır başlıklarının hem birincil üst bilgi, hem de tüm destekleyici üstbilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6ddf-116">Bu kavram, korumalı hale bir [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] burada bir kullanıcının belirlediği bir "Ad" sütununu elektronik tablo.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-116">This concept becomes evident in a [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="b6ddf-117">Bu artık iki Üstbilgi sütununda — kullanıcı ve uygulama tarafından atanan bu sütun için alfasayısal ataması tarafından tanımlanan "Ad" başlığı.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
-   <span data-ttu-id="b6ddf-118">Bkz: [UI Otomasyon kılavuz denetim düzenini uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) ilgili kılavuz işlevselliği için.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-118">See [Implementing the UI Automation Grid Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="b6ddf-119">![Karmaşık üstbilgi öğeleri içeren tablo. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="b6ddf-119">![Table with complex header items.](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="b6ddf-120">Karmaşık sütun üst bilgileri içeren bir tablo örneği</span><span class="sxs-lookup"><span data-stu-id="b6ddf-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="b6ddf-121">![Tablo Belirsiz RowOrColumnMajor özelliğine sahip. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="b6ddf-121">![Table with ambiguous RowOrColumnMajor property.](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="b6ddf-122">Belirsiz RowOrColumnMajor özelliğine sahip bir tablo örneği</span><span class="sxs-lookup"><span data-stu-id="b6ddf-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="b6ddf-123">Gerekli üyeleri ITableProvider için</span><span class="sxs-lookup"><span data-stu-id="b6ddf-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="b6ddf-124">Aşağıdaki özellikleri ve yöntemleri için ITableProvider arabirimi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="b6ddf-125">Gerekli üyeleri</span><span class="sxs-lookup"><span data-stu-id="b6ddf-125">Required members</span></span>|<span data-ttu-id="b6ddf-126">Üye türü</span><span class="sxs-lookup"><span data-stu-id="b6ddf-126">Member type</span></span>|<span data-ttu-id="b6ddf-127">Notlar</span><span class="sxs-lookup"><span data-stu-id="b6ddf-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="b6ddf-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="b6ddf-128">Property</span></span>|<span data-ttu-id="b6ddf-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="b6ddf-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b6ddf-130">Method</span></span>|<span data-ttu-id="b6ddf-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="b6ddf-132">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b6ddf-132">Method</span></span>|<span data-ttu-id="b6ddf-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-133">None</span></span>|  
  
 <span data-ttu-id="b6ddf-134">Bu denetim düzeni ilişkili olay vardır.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="b6ddf-135">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="b6ddf-135">Exceptions</span></span>  
 <span data-ttu-id="b6ddf-136">Bu denetim düzeni ilişkili hiçbir özel durum vardır.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ddf-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6ddf-137">See Also</span></span>  
 [<span data-ttu-id="b6ddf-138">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b6ddf-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="b6ddf-139">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="b6ddf-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="b6ddf-140">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="b6ddf-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="b6ddf-141">UI Otomasyonu TableItem Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="b6ddf-141">Implementing the UI Automation TableItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [<span data-ttu-id="b6ddf-142">UI Otomasyonu Grid Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="b6ddf-142">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="b6ddf-143">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b6ddf-143">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="b6ddf-144">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="b6ddf-144">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
