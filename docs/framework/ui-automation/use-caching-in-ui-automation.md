---
title: "UI Otomasyonda Önbelleğe Almayı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 808ba16cbacfad2cc255ae40e2cbad3178350afc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="34efc-102">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="34efc-102">Use Caching in UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="34efc-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="34efc-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="34efc-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="34efc-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="34efc-105">Bu bölümde, önbelleğe alınmasını uygulamak gösterilmiştir <xref:System.Windows.Automation.AutomationElement> özellikleri ve denetim düzenleri.</span><span class="sxs-lookup"><span data-stu-id="34efc-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="34efc-106">Bir önbellek isteği etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="34efc-106">Activate a Cache Request</span></span>  
  
1.  <span data-ttu-id="34efc-107">Oluşturma bir <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="34efc-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="34efc-108">Kullanarak özellikleri ve önbellek desenlerini belirtin <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="34efc-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3.  <span data-ttu-id="34efc-109">Ayarlayarak önbelleğe alma kapsamını belirtin <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="34efc-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4.  <span data-ttu-id="34efc-110">Alt ağaç görünümünü ayarlayarak belirtin <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="34efc-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5.  <span data-ttu-id="34efc-111">Ayarlama <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> özelliğine <xref:System.Windows.Automation.AutomationElementMode.None> nesneleri için tam bir başvuru almadığınızdan verimliliğini artırmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="34efc-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="34efc-112">(Bu, geçerli değerleri bu nesnelerden almak mümkün hale getirir.)</span><span class="sxs-lookup"><span data-stu-id="34efc-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6.  <span data-ttu-id="34efc-113">İstek kullanarak etkinleştirme <xref:System.Windows.Automation.CacheRequest.Activate%2A> içinde bir `using` blok (`Using` içinde [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="34efc-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).</span></span>  
  
 <span data-ttu-id="34efc-114">Alma sonra <xref:System.Windows.Automation.AutomationElement> nesneleri veya olaylara abone olma devre dışı bırakma isteği kullanarak <xref:System.Windows.Automation.CacheRequest.Pop%2A> (varsa <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanılan) veya tarafından oluşturulan nesne atma <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="34efc-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="34efc-115">(Kullanım <xref:System.Windows.Automation.CacheRequest.Activate%2A> içinde bir `using` blok (`Using` içinde [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="34efc-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="34efc-116">Önbellek AutomationElement özellikleri</span><span class="sxs-lookup"><span data-stu-id="34efc-116">Cache AutomationElement Properties</span></span>  
  
1.  <span data-ttu-id="34efc-117">Sırada bir <xref:System.Windows.Automation.CacheRequest> etkindir elde <xref:System.Windows.Automation.AutomationElement> kullanarak nesneleri <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; veya elde bir <xref:System.Windows.Automation.AutomationElement> için ne zaman kayıtlı bir olay kaynağı olarak <xref:System.Windows.Automation.CacheRequest> etkin olduğu.</span><span class="sxs-lookup"><span data-stu-id="34efc-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="34efc-118">(Bir önbellek geçirerek oluşturabilirsiniz bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache veya birini <xref:System.Windows.Automation.TreeWalker> yöntemleri.)</span><span class="sxs-lookup"><span data-stu-id="34efc-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2.  <span data-ttu-id="34efc-119">Kullanım <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> veya bir özellikten almak <xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="34efc-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="34efc-120">Önbelleğe alınan desenleri ve bunların özelliklerini alın</span><span class="sxs-lookup"><span data-stu-id="34efc-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1.  <span data-ttu-id="34efc-121">Sırada bir <xref:System.Windows.Automation.CacheRequest> etkindir elde <xref:System.Windows.Automation.AutomationElement> kullanarak nesneleri <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; veya elde bir <xref:System.Windows.Automation.AutomationElement> için ne zaman kayıtlı bir olay kaynağı olarak <xref:System.Windows.Automation.CacheRequest> etkin olduğu.</span><span class="sxs-lookup"><span data-stu-id="34efc-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="34efc-122">(Bir önbellek geçirerek oluşturabilirsiniz bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache veya birini <xref:System.Windows.Automation.TreeWalker> yöntemleri.)</span><span class="sxs-lookup"><span data-stu-id="34efc-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2.  <span data-ttu-id="34efc-123">Kullanım <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> önbelleğe alınmış desen alınamadı.</span><span class="sxs-lookup"><span data-stu-id="34efc-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3.  <span data-ttu-id="34efc-124">Özellik değerleri almak `Cached` denetim düzeni özelliği.</span><span class="sxs-lookup"><span data-stu-id="34efc-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34efc-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="34efc-125">Example</span></span>  
 <span data-ttu-id="34efc-126">Aşağıdaki kod örneği kullanarak önbelleğe alma, çeşitli yönlerini gösterir <xref:System.Windows.Automation.CacheRequest.Activate%2A> etkinleştirmek için <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="34efc-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="34efc-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="34efc-127">Example</span></span>  
 <span data-ttu-id="34efc-128">Aşağıdaki kod örneği kullanarak önbelleğe alma, çeşitli yönlerini gösterir <xref:System.Windows.Automation.CacheRequest.Push%2A> etkinleştirmek için <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="34efc-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="34efc-129">Önbellek isteği iç içe istediğinizde, kullanmak için tercih edilir dışında <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="34efc-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="34efc-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34efc-130">See Also</span></span>  
 [<span data-ttu-id="34efc-131">UI Otomasyonu İstemcilerinde Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="34efc-131">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
