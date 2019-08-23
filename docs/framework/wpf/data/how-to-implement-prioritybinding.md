---
title: 'Nasıl yapılır: PriorityBinding Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: ad19db9d686469e3ade1ff188553fceb8d525674
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937441"
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="bb44d-102">Nasıl yapılır: PriorityBinding Uygulama</span><span class="sxs-lookup"><span data-stu-id="bb44d-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="bb44d-103"><xref:System.Windows.Data.PriorityBinding>' [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de bir bağlama listesi belirterek.</span><span class="sxs-lookup"><span data-stu-id="bb44d-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="bb44d-104">Bağlamaların listesi, en yüksek öncelikten en düşük önceliğe göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="bb44d-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="bb44d-105">En yüksek öncelikli bağlama işlendiğinde başarıyla bir değer döndürürse, listedeki diğer bağlamaları işlemeye hiçbir zaman gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="bb44d-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="bb44d-106">En yüksek öncelikli bağlamanın değerlendirilmesi uzun zaman alacağından, daha yüksek bir öncelik bağlamasının bir değeri başarıyla döndürünceye kadar bir değer döndüren bir sonraki en yüksek öncelik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb44d-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb44d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb44d-107">Example</span></span>  
 <span data-ttu-id="bb44d-108">Nasıl <xref:System.Windows.Data.PriorityBinding> çalıştığını göstermek için `AsyncDataSource` , nesnesi aşağıdaki üç özelliklerle oluşturulmuştur: `FastDP`, `SlowerDP`ve `SlowestDP`.</span><span class="sxs-lookup"><span data-stu-id="bb44d-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="bb44d-109">Get erişimcisi `FastDP` , `_fastDP` veri üyesinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb44d-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="bb44d-110">Get erişimcisi `SlowerDP` , `_slowerDP` veri üyesinin değerini döndürmeden önce 3 saniye bekler.</span><span class="sxs-lookup"><span data-stu-id="bb44d-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="bb44d-111">Get erişimcisi `SlowestDP` , `_slowestDP` veri üyesinin değerini döndürmeden önce 5 saniye bekler.</span><span class="sxs-lookup"><span data-stu-id="bb44d-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb44d-112">Bu örnek yalnızca tanıtım amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="bb44d-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="bb44d-113">Yönergeler [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] , bir alan kümesinden daha yavaş büyüklüğü olan özellikleri tanımlamaya karşı önerilir.</span><span class="sxs-lookup"><span data-stu-id="bb44d-113">The [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="bb44d-114">Daha fazla bilgi için bkz. [Özellikler ve yöntemler arasında seçim yapma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bb44d-114">For more information, see [Choosing Between Properties and Methods](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span></span>  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="bb44d-115"><xref:System.Windows.Controls.TextBlock.Text%2A> Özelliği `AsyncDS` kullanarak yukarıya<xref:System.Windows.Data.PriorityBinding>bağlar:</span><span class="sxs-lookup"><span data-stu-id="bb44d-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="bb44d-116">Bağlama altyapısı <xref:System.Windows.Data.Binding> nesneleri işlediğinde, `SlowestDP` özelliği ile <xref:System.Windows.Data.Binding>başlar, bu, özelliğe bağlanır.</span><span class="sxs-lookup"><span data-stu-id="bb44d-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="bb44d-117">Bu işlendiğinde <xref:System.Windows.Data.Binding> , 5 saniye boyunca uymadığı için bir değeri başarıyla döndürmez, bu nedenle sonraki <xref:System.Windows.Data.Binding> öğe işlenir.</span><span class="sxs-lookup"><span data-stu-id="bb44d-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="bb44d-118">Sonraki <xref:System.Windows.Data.Binding> bir değer, 3 saniye boyunca uyurken bir değeri başarıyla döndürmez.</span><span class="sxs-lookup"><span data-stu-id="bb44d-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="bb44d-119">Bağlama altyapısı daha sonra <xref:System.Windows.Data.Binding> `FastDP` özelliğe bağlantılı olan bir sonraki öğeye gider.</span><span class="sxs-lookup"><span data-stu-id="bb44d-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="bb44d-120">Bu <xref:System.Windows.Data.Binding> , "Fast Value" değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb44d-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="bb44d-121"><xref:System.Windows.Controls.TextBlock> Şimdi "hızlı değer" değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb44d-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="bb44d-122">3 saniye dolduktan sonra, `SlowerDP` özelliği "daha yavaş değer" değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb44d-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="bb44d-123"><xref:System.Windows.Controls.TextBlock> Sonra "daha yavaş değer" değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb44d-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="bb44d-124">5 saniye geçtikten sonra, `SlowestDP` özelliği "en yavaş değer" değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb44d-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="bb44d-125">İlk olarak listelenen bu bağlama en yüksek önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bb44d-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="bb44d-126"><xref:System.Windows.Controls.TextBlock> Şimdi "en yavaş değer" değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb44d-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="bb44d-127">Bir <xref:System.Windows.Data.PriorityBinding> bağlamadan başarılı bir dönüş değeri olarak kabul edilen özellikler hakkında bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="bb44d-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb44d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb44d-128">See also</span></span>

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bb44d-129">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bb44d-129">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="bb44d-130">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="bb44d-130">How-to Topics</span></span>](data-binding-how-to-topics.md)
