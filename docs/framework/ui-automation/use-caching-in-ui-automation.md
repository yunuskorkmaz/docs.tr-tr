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
ms.openlocfilehash: dd7506d388ba215f671ee3c7c4bae09baf4cc2b3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040317"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="9fdd4-102">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="9fdd4-102">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="9fdd4-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9fdd4-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="9fdd4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9fdd4-105">Bu bölümde, <xref:System.Windows.Automation.AutomationElement> özelliklerin ve denetim desenlerinin önbelleğe alınmasının nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="9fdd4-106">Önbellek Isteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9fdd4-106">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="9fdd4-107">Oluşturma bir <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="9fdd4-108">Kullanarak <xref:System.Windows.Automation.CacheRequest.Add%2A>önbelleğe almak için özellikleri ve desenleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="9fdd4-109"><xref:System.Windows.Automation.CacheRequest.TreeScope%2A> Özelliği ayarlayarak önbelleğe alma kapsamını belirtin.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="9fdd4-110"><xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> Özelliği ayarlayarak alt ağacın görünümünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="9fdd4-111">Nesnelere tam <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> başvuru almadıkça verimliliği artırmak istiyorsanız, özelliğini olarak <xref:System.Windows.Automation.AutomationElementMode.None> ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="9fdd4-112">(Bu, bu nesnelerden geçerli değerleri almayı olanaksız hale getirir.)</span><span class="sxs-lookup"><span data-stu-id="9fdd4-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="9fdd4-113">`Using` Bir <xref:System.Windows.Automation.CacheRequest.Activate%2A> blokiçinde`using` kullanarak isteği etkinleştirin (Microsoft Visual Basic .net 'te).</span><span class="sxs-lookup"><span data-stu-id="9fdd4-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="9fdd4-114">Nesneleri aldıktan <xref:System.Windows.Automation.AutomationElement> veya olaylara abone olduktan sonra <xref:System.Windows.Automation.CacheRequest.Pop%2A> ( <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanıldıysa) veya tarafından <xref:System.Windows.Automation.CacheRequest.Activate%2A>oluşturulan nesneyi elden kaldırarak isteği devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="9fdd4-115">(Bir <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloğunda kullanın (`Using` Microsoft Visual Basic .net 'te).</span><span class="sxs-lookup"><span data-stu-id="9fdd4-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="9fdd4-116">Önbellek AutomationElement özellikleri</span><span class="sxs-lookup"><span data-stu-id="9fdd4-116">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="9fdd4-117"><xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElement> Etkin olsa da, veya <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> kullanarak<xref:System.Windows.Automation.AutomationElement.FindAll%2A>nesneleri elde edin ya da, etkin olduğunda için kaydettiğiniz bir olayın kaynağı olarak elde edin. <xref:System.Windows.Automation.CacheRequest></span><span class="sxs-lookup"><span data-stu-id="9fdd4-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="9fdd4-118">(Bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e veya <xref:System.Windows.Automation.TreeWalker> yöntemlerinden birine geçirerek de bir önbellek oluşturabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="9fdd4-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="9fdd4-119">Öğesinin <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> özelliğindenbir<xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği kullanın veya alın. <xref:System.Windows.Automation.AutomationElement></span><span class="sxs-lookup"><span data-stu-id="9fdd4-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="9fdd4-120">Önbelleğe alınmış desenleri ve bunların özelliklerini alma</span><span class="sxs-lookup"><span data-stu-id="9fdd4-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="9fdd4-121"><xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElement> Etkin olsa da, veya <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> kullanarak<xref:System.Windows.Automation.AutomationElement.FindAll%2A>nesneleri elde edin ya da, etkin olduğunda için kaydettiğiniz bir olayın kaynağı olarak elde edin. <xref:System.Windows.Automation.CacheRequest></span><span class="sxs-lookup"><span data-stu-id="9fdd4-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="9fdd4-122">(Bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e veya <xref:System.Windows.Automation.TreeWalker> yöntemlerinden birine geçirerek de bir önbellek oluşturabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="9fdd4-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="9fdd4-123">Önbelleğe <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> alınmış <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> bir model almak için veya kullanın.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="9fdd4-124">Denetim deseninin `Cached` özelliğinden özellik değerlerini alın.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fdd4-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fdd4-125">Example</span></span>  
 <span data-ttu-id="9fdd4-126">Aşağıdaki kod örneği, öğesini <xref:System.Windows.Automation.CacheRequest.Activate%2A> <xref:System.Windows.Automation.CacheRequest>etkinleştirmek için kullanarak, önbelleğe alma işleminin çeşitli yönlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="9fdd4-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fdd4-127">Example</span></span>  
 <span data-ttu-id="9fdd4-128">Aşağıdaki kod örneği, öğesini <xref:System.Windows.Automation.CacheRequest.Push%2A> <xref:System.Windows.Automation.CacheRequest>etkinleştirmek için kullanarak, önbelleğe alma işleminin çeşitli yönlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="9fdd4-129">Önbellek isteklerini iç içe aktarmak istediğiniz durumlar dışında, kullanılması <xref:System.Windows.Automation.CacheRequest.Activate%2A>tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="9fdd4-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fdd4-130">See also</span></span>

- [<span data-ttu-id="9fdd4-131">UI Otomasyonu İstemcilerinde Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="9fdd4-131">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
