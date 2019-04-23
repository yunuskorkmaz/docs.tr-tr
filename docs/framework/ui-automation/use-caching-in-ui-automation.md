---
title: UI Otomasyonda Önbelleğe Almayı Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: b63d94789d081ce7337b5f9c2abca3f7d9e99eeb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308672"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="e3590-102">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="e3590-102">Use Caching in UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="e3590-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e3590-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e3590-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e3590-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e3590-105">Bu bölümde, önbelleğe almayı uygulayın gösterilmektedir <xref:System.Windows.Automation.AutomationElement> özellikleri ve denetim desenleri.</span><span class="sxs-lookup"><span data-stu-id="e3590-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="e3590-106">Bir önbellek isteği'ni etkinleştirin</span><span class="sxs-lookup"><span data-stu-id="e3590-106">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="e3590-107">Oluşturma bir <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="e3590-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="e3590-108">Özellikler ve önbellek desenlerini kullanarak belirtin <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="e3590-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="e3590-109">Ayarlayarak önbelleğe alma kapsamı belirle <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e3590-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="e3590-110">Alt ağaç görünümünü belirtmek <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e3590-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="e3590-111">Ayarlama <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> özelliğini <xref:System.Windows.Automation.AutomationElementMode.None> nesneleri için tam bir başvuru almayarak verimliliği artırmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="e3590-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="e3590-112">(Bu, bu nesnelerden geçerli değerleri almak imkansız hale getirir.)</span><span class="sxs-lookup"><span data-stu-id="e3590-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="e3590-113">Etkinleştirme isteği kullanarak <xref:System.Windows.Automation.CacheRequest.Activate%2A> içinde bir `using` blok (`Using` Microsoft Visual Basic. NET'te).</span><span class="sxs-lookup"><span data-stu-id="e3590-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="e3590-114">Aldıktan sonra <xref:System.Windows.Automation.AutomationElement> nesneleri veya olaylara abone olma devre dışı bırakma isteği kullanarak <xref:System.Windows.Automation.CacheRequest.Pop%2A> (varsa <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanıldı) ya da tarafından oluşturulan nesne disposing <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e3590-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="e3590-115">(Kullanım <xref:System.Windows.Automation.CacheRequest.Activate%2A> içinde bir `using` blok (`Using` Microsoft Visual Basic. NET'te).</span><span class="sxs-lookup"><span data-stu-id="e3590-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="e3590-116">Önbellek AutomationElement özellikleri</span><span class="sxs-lookup"><span data-stu-id="e3590-116">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="e3590-117">Sırasında bir <xref:System.Windows.Automation.CacheRequest> etkin olup elde <xref:System.Windows.Automation.AutomationElement> kullanarak nesneleri <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; veya bir <xref:System.Windows.Automation.AutomationElement> için kayıtlı bir olay kaynağı olarak <xref:System.Windows.Automation.CacheRequest> etkindi.</span><span class="sxs-lookup"><span data-stu-id="e3590-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="e3590-118">(Geçirerek bir önbellek oluşturabilirsiniz bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache ya da birini <xref:System.Windows.Automation.TreeWalker> yöntemler.)</span><span class="sxs-lookup"><span data-stu-id="e3590-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="e3590-119">Kullanım <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> veya bir özelliği almak <xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="e3590-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="e3590-120">Önbelleğe alınan desenleri ve bunların özelliklerini alın</span><span class="sxs-lookup"><span data-stu-id="e3590-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="e3590-121">Sırasında bir <xref:System.Windows.Automation.CacheRequest> etkin olup elde <xref:System.Windows.Automation.AutomationElement> kullanarak nesneleri <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; veya bir <xref:System.Windows.Automation.AutomationElement> için kayıtlı bir olay kaynağı olarak <xref:System.Windows.Automation.CacheRequest> etkindi.</span><span class="sxs-lookup"><span data-stu-id="e3590-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="e3590-122">(Geçirerek bir önbellek oluşturabilirsiniz bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache ya da birini <xref:System.Windows.Automation.TreeWalker> yöntemler.)</span><span class="sxs-lookup"><span data-stu-id="e3590-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="e3590-123">Kullanım <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> önbelleğe alınmış bir deseni alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="e3590-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="e3590-124">Özellik değerleri almak `Cached` denetim düzeni özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="e3590-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3590-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3590-125">Example</span></span>  
 <span data-ttu-id="e3590-126">Aşağıdaki kod örneği kullanarak önbelleğe alma, çeşitli yönlerini gösteren <xref:System.Windows.Automation.CacheRequest.Activate%2A> etkinleştirmek için <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="e3590-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="e3590-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3590-127">Example</span></span>  
 <span data-ttu-id="e3590-128">Aşağıdaki kod örneği kullanarak önbelleğe alma, çeşitli yönlerini gösteren <xref:System.Windows.Automation.CacheRequest.Push%2A> etkinleştirmek için <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="e3590-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="e3590-129">Önbellek isteği'iç içe istediklerinde kullanmak tercih edilir dışında <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="e3590-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="e3590-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3590-130">See also</span></span>

- [<span data-ttu-id="e3590-131">UI Otomasyonu İstemcilerinde Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="e3590-131">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
