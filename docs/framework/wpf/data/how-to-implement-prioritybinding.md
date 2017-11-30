---
title: "Nasıl yapılır: PriorityBinding Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9753462908928eaf177e100a16186826bf4828ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="1c8d6-102">Nasıl yapılır: PriorityBinding Uygulama</span><span class="sxs-lookup"><span data-stu-id="1c8d6-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="1c8d6-103"><xref:System.Windows.Data.PriorityBinding>içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bağlamaların listesini belirterek çalışır.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="1c8d6-104">Bağlama Listesi en yüksek öncelikli olandan en düşük önceliği sıralanır.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="1c8d6-105">Yüksek önceliği olan bağlama bir değer döndürürse başarıyla işlendiğinde yoktur hiçbir zaman listedeki diğer bağlamaları işlem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="1c8d6-106">En yüksek öncelik bağlama değerlendirilmesi uzun süren durum olabilir, bir daha yüksek bir öncelik değeri başarıyla döndürünceye kadar başarılı bir şekilde bir değer döndüren bir sonraki en yüksek öncelikli kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c8d6-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c8d6-107">Example</span></span>  
 <span data-ttu-id="1c8d6-108">Göstermek için nasıl <xref:System.Windows.Data.PriorityBinding> çalışır, `AsyncDataSource` nesnesi şu üç özellik ile oluşturuldu: `FastDP`, `SlowerDP`, ve `SlowestDP`.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="1c8d6-109">Get erişimcisine `FastDP` değerini döndürür `_fastDP` veri üyesi.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="1c8d6-110">Get erişimcisine `SlowerDP` değerini dönmeden önce 3 saniye bekler `_slowerDP` veri üyesi.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="1c8d6-111">Get erişimcisine `SlowestDP` değerini dönmeden önce 5 saniye bekler `_slowestDP` veri üyesi.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c8d6-112">Bu örnek, yalnızca tanıtım amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="1c8d6-113">[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] Yönergeleri büyüklük alan kümesinden daha yavaş olan özellikleri tanımlamaya karşı önerilir.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="1c8d6-114">Daha fazla bilgi için bkz: [NIB: seçme arasında özellikleri ve yöntemleri](http://msdn.microsoft.com/en-us/55825e8f-7e2e-448a-9505-7217cc91b1af).</span><span class="sxs-lookup"><span data-stu-id="1c8d6-114">For more information, see [NIB: Choosing Between Properties and Methods](http://msdn.microsoft.com/en-us/55825e8f-7e2e-448a-9505-7217cc91b1af).</span></span>  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="1c8d6-115"><xref:System.Windows.Controls.TextBlock.Text%2A> Özelliğini bağlar yukarıdaki `AsyncDS` kullanarak <xref:System.Windows.Data.PriorityBinding>:</span><span class="sxs-lookup"><span data-stu-id="1c8d6-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="1c8d6-116">Bağlama altyapısı işlediğinde <xref:System.Windows.Data.Binding> nesneleri, ilk başlar <xref:System.Windows.Data.Binding>, bağlı `SlowestDP` özelliği.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="1c8d6-117">Zaman bu <xref:System.Windows.Data.Binding> olduğundan, 5 saniye kadar sonraki uyku için işlenen, bir değer başarıyla dönmez <xref:System.Windows.Data.Binding> öğesi işlenir.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="1c8d6-118">Sonraki <xref:System.Windows.Data.Binding> 3 saniye için uyuyor için bir değer başarıyla döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="1c8d6-119">Bağlama altyapısı ardından sonraki taşır <xref:System.Windows.Data.Binding> bağlı öğesi `FastDP` özelliği.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="1c8d6-120">Bu <xref:System.Windows.Data.Binding> "Fast Value" değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="1c8d6-121"><xref:System.Windows.Controls.TextBlock> Şimdi value "Hızlı" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="1c8d6-122">3 saniye geçtikten sonra `SlowerDP` özelliği "Yavaş Value" değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="1c8d6-123"><xref:System.Windows.Controls.TextBlock> "Yavaş value" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="1c8d6-124">5 saniye geçtikten sonra `SlowestDP` özelliği "Yavaş Value" değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="1c8d6-125">İlk listelenmediğinden Bu bağlama en yüksek önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="1c8d6-126"><xref:System.Windows.Controls.TextBlock> Şimdi "yavaş value" değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="1c8d6-127">Bkz: <xref:System.Windows.Data.PriorityBinding> bağlama gelen başarılı bir dönüş değeri olarak kabul hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8d6-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c8d6-128">See Also</span></span>  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1c8d6-129">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="1c8d6-129">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="1c8d6-130">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="1c8d6-130">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
