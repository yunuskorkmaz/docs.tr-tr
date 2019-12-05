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
ms.openlocfilehash: 679192b611a423e095ee9acc956d247364940edf
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800802"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="7a2d3-102">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="7a2d3-102">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="7a2d3-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7a2d3-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="7a2d3-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="7a2d3-105">Bu bölümde, <xref:System.Windows.Automation.AutomationElement> özelliklerinin ve denetim desenlerinin önbelleğe alınmasının nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="7a2d3-106">Önbellek Isteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7a2d3-106">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="7a2d3-107">Oluşturma bir <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="7a2d3-108"><xref:System.Windows.Automation.CacheRequest.Add%2A>kullanarak önbelleğe almak için özellikleri ve desenleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="7a2d3-109"><xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliğini ayarlayarak önbelleğe alma kapsamını belirtin.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="7a2d3-110"><xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> özelliğini ayarlayarak alt ağacın görünümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="7a2d3-111">Nesnelere tam bir başvuru almadıkça verimliliği artırmak istiyorsanız, <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> özelliğini <xref:System.Windows.Automation.AutomationElementMode.None> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="7a2d3-112">(Bu, bu nesnelerden geçerli değerleri almayı olanaksız hale getirir.)</span><span class="sxs-lookup"><span data-stu-id="7a2d3-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="7a2d3-113">`using` bloğunda <xref:System.Windows.Automation.CacheRequest.Activate%2A> kullanarak isteği etkinleştirin (Microsoft Visual Basic .NET 'te`Using`).</span><span class="sxs-lookup"><span data-stu-id="7a2d3-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="7a2d3-114"><xref:System.Windows.Automation.AutomationElement> nesneleri aldıktan veya olaylara abone olduktan sonra, <xref:System.Windows.Automation.CacheRequest.Pop%2A> kullanarak (<xref:System.Windows.Automation.CacheRequest.Push%2A> kullanıldıysa) veya <xref:System.Windows.Automation.CacheRequest.Activate%2A>tarafından oluşturulan nesneyi elden kaldırarak isteği devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="7a2d3-115">(Microsoft Visual Basic .NET 'te <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloğunda kullanın (`Using`).</span><span class="sxs-lookup"><span data-stu-id="7a2d3-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="7a2d3-116">Önbellek AutomationElement özellikleri</span><span class="sxs-lookup"><span data-stu-id="7a2d3-116">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="7a2d3-117"><xref:System.Windows.Automation.CacheRequest> etkinken, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>kullanarak <xref:System.Windows.Automation.AutomationElement> nesneleri elde edin; veya <xref:System.Windows.Automation.CacheRequest> etkinken için kaydettiğiniz bir olayın kaynağı olarak bir <xref:System.Windows.Automation.AutomationElement> edinin.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="7a2d3-118">(Ayrıca bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e geçirerek veya <xref:System.Windows.Automation.TreeWalker> metotlarından birine bir önbellek oluşturabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="7a2d3-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="7a2d3-119"><xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> kullanın veya <xref:System.Windows.Automation.AutomationElement><xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliğinden bir özellik alın.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="7a2d3-120">Önbelleğe alınmış desenleri ve bunların özelliklerini alma</span><span class="sxs-lookup"><span data-stu-id="7a2d3-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="7a2d3-121"><xref:System.Windows.Automation.CacheRequest> etkinken, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>kullanarak <xref:System.Windows.Automation.AutomationElement> nesneleri elde edin; veya <xref:System.Windows.Automation.CacheRequest> etkinken için kaydettiğiniz bir olayın kaynağı olarak bir <xref:System.Windows.Automation.AutomationElement> edinin.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="7a2d3-122">(Ayrıca bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e geçirerek veya <xref:System.Windows.Automation.TreeWalker> metotlarından birine bir önbellek oluşturabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="7a2d3-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="7a2d3-123">Önbelleğe alınmış bir model almak için <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> kullanın.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="7a2d3-124">Denetim deseninin `Cached` özelliğinden özellik değerlerini alın.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a2d3-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a2d3-125">Example</span></span>  
 <span data-ttu-id="7a2d3-126">Aşağıdaki kod örneği, <xref:System.Windows.Automation.CacheRequest>etkinleştirmek için <xref:System.Windows.Automation.CacheRequest.Activate%2A> kullanarak önbelleğe alma işleminin çeşitli yönlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="7a2d3-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a2d3-127">Example</span></span>  
 <span data-ttu-id="7a2d3-128">Aşağıdaki kod örneği, <xref:System.Windows.Automation.CacheRequest>etkinleştirmek için <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanarak önbelleğe alma işleminin çeşitli yönlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="7a2d3-129">Önbellek isteklerini iç içe aktarmak istediğiniz durumlar dışında <xref:System.Windows.Automation.CacheRequest.Activate%2A>kullanmak tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="7a2d3-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a2d3-130">See also</span></span>

- [<span data-ttu-id="7a2d3-131">UI Otomasyonu İstemcilerinde Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="7a2d3-131">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
