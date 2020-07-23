---
title: UI Otomasyonda Önbelleğe Almayı Kullanma
description: Bkz. Kullanıcı Arabirimi Otomasyonu 'nda önbelleğe alma kullanma. Önbellek isteğini etkinleştirme, AutomationElement özelliklerini önbelleğe alma ve önbelleğe alınmış desenler alma adımlarını gözden geçirin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 8dff9db77e39dc66a16b6a7b395c76a3c768d48e
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924493"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="bdcda-104">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="bdcda-104">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="bdcda-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bdcda-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="bdcda-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bdcda-107">Bu bölümde, <xref:System.Windows.Automation.AutomationElement> özelliklerin ve denetim desenlerinin önbelleğe alınmasının nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bdcda-107">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="bdcda-108">Önbellek Isteğini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="bdcda-108">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="bdcda-109">Oluşturun <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-109">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="bdcda-110">Kullanarak önbelleğe almak için özellikleri ve desenleri belirtin <xref:System.Windows.Automation.CacheRequest.Add%2A> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-110">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="bdcda-111">Özelliği ayarlayarak önbelleğe alma kapsamını belirtin <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-111">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="bdcda-112">Özelliği ayarlayarak alt ağacın görünümünü belirtin <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-112">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="bdcda-113"><xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> <xref:System.Windows.Automation.AutomationElementMode.None> Nesnelere tam başvuru almadıkça verimliliği artırmak istiyorsanız, özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bdcda-113">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="bdcda-114">(Bu, bu nesnelerden geçerli değerleri almayı olanaksız hale getirir.)</span><span class="sxs-lookup"><span data-stu-id="bdcda-114">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="bdcda-115"><xref:System.Windows.Automation.CacheRequest.Activate%2A>Bir blok içinde kullanarak isteği etkinleştirin `using` ( `Using` Microsoft Visual Basic .net 'te).</span><span class="sxs-lookup"><span data-stu-id="bdcda-115">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="bdcda-116">Nesneleri aldıktan <xref:System.Windows.Automation.AutomationElement> veya olaylara abone olduktan sonra <xref:System.Windows.Automation.CacheRequest.Pop%2A> ( <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanıldıysa) veya tarafından oluşturulan nesneyi elden kaldırarak isteği devre dışı bırakın <xref:System.Windows.Automation.CacheRequest.Activate%2A> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-116">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="bdcda-117">( <xref:System.Windows.Automation.CacheRequest.Activate%2A> Bir bloğunda kullanın `using` ( `Using` Microsoft Visual Basic .net 'te).</span><span class="sxs-lookup"><span data-stu-id="bdcda-117">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="bdcda-118">Önbellek AutomationElement özellikleri</span><span class="sxs-lookup"><span data-stu-id="bdcda-118">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="bdcda-119">Etkin olsa <xref:System.Windows.Automation.CacheRequest> da, <xref:System.Windows.Automation.AutomationElement> veya kullanarak nesneleri elde edin <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ya da <xref:System.Windows.Automation.AutomationElement> , etkin olduğunda için kaydettiğiniz bir olayın kaynağı olarak elde edin <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-119">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="bdcda-120">(Bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e veya yöntemlerinden birine geçirerek de bir önbellek oluşturabilirsiniz <xref:System.Windows.Automation.TreeWalker> .)</span><span class="sxs-lookup"><span data-stu-id="bdcda-120">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="bdcda-121"><xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>Öğesinin özelliğinden bir özelliği kullanın veya alın <xref:System.Windows.Automation.AutomationElement.Cached%2A> <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-121">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="bdcda-122">Önbelleğe alınmış desenleri ve bunların özelliklerini alma</span><span class="sxs-lookup"><span data-stu-id="bdcda-122">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="bdcda-123">Etkin olsa <xref:System.Windows.Automation.CacheRequest> da, <xref:System.Windows.Automation.AutomationElement> veya kullanarak nesneleri elde edin <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ya da <xref:System.Windows.Automation.AutomationElement> , etkin olduğunda için kaydettiğiniz bir olayın kaynağı olarak elde edin <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-123">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="bdcda-124">(Bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e veya yöntemlerinden birine geçirerek de bir önbellek oluşturabilirsiniz <xref:System.Windows.Automation.TreeWalker> .)</span><span class="sxs-lookup"><span data-stu-id="bdcda-124">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="bdcda-125"><xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> Önbelleğe alınmış bir model almak için veya kullanın.</span><span class="sxs-lookup"><span data-stu-id="bdcda-125">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="bdcda-126">`Cached`Denetim deseninin özelliğinden özellik değerlerini alın.</span><span class="sxs-lookup"><span data-stu-id="bdcda-126">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdcda-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdcda-127">Example</span></span>  
 <span data-ttu-id="bdcda-128">Aşağıdaki kod örneği, öğesini etkinleştirmek için kullanarak, önbelleğe alma işleminin çeşitli yönlerini gösterir <xref:System.Windows.Automation.CacheRequest.Activate%2A> <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="bdcda-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdcda-129">Example</span></span>  
 <span data-ttu-id="bdcda-130">Aşağıdaki kod örneği, öğesini etkinleştirmek için kullanarak, önbelleğe alma işleminin çeşitli yönlerini gösterir <xref:System.Windows.Automation.CacheRequest.Push%2A> <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-130">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="bdcda-131">Önbellek isteklerini iç içe aktarmak istediğiniz durumlar dışında, kullanılması tercih edilir <xref:System.Windows.Automation.CacheRequest.Activate%2A> .</span><span class="sxs-lookup"><span data-stu-id="bdcda-131">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="bdcda-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdcda-132">See also</span></span>

- [<span data-ttu-id="bdcda-133">UI Otomasyonda Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="bdcda-133">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
