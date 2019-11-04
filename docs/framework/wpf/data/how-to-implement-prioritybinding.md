---
title: 'Nasıl yapılır: PriorityBinding Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: 343b0aca4736905f3a0cbff5a0f76b170da0c920
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459788"
---
# <a name="how-to-implement-prioritybinding"></a><span data-ttu-id="79041-102">Nasıl yapılır: PriorityBinding Uygulama</span><span class="sxs-lookup"><span data-stu-id="79041-102">How to: Implement PriorityBinding</span></span>
<span data-ttu-id="79041-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Data.PriorityBinding>, bağlamaların bir listesini belirterek işe yarar.</span><span class="sxs-lookup"><span data-stu-id="79041-103"><xref:System.Windows.Data.PriorityBinding> in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] works by specifying a list of bindings.</span></span> <span data-ttu-id="79041-104">Bağlamaların listesi, en yüksek öncelikten en düşük önceliğe göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="79041-104">The list of bindings is ordered from highest priority to lowest priority.</span></span> <span data-ttu-id="79041-105">En yüksek öncelikli bağlama işlendiğinde başarıyla bir değer döndürürse, listedeki diğer bağlamaları işlemeye hiçbir zaman gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="79041-105">If the highest priority binding returns a value successfully when it is processed then there is never a need to process the other bindings in the list.</span></span> <span data-ttu-id="79041-106">En yüksek öncelikli bağlamanın değerlendirilmesi uzun zaman alacağından, daha yüksek bir öncelik bağlamasının bir değeri başarıyla döndürünceye kadar bir değer döndüren bir sonraki en yüksek öncelik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79041-106">It could be the case that the highest priority binding takes a long time to be evaluated, the next highest priority that returns a value successfully will be used until a binding of a higher priority returns a value successfully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79041-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="79041-107">Example</span></span>  
 <span data-ttu-id="79041-108"><xref:System.Windows.Data.PriorityBinding> nasıl çalıştığını göstermek için, `AsyncDataSource` nesnesi şu üç özellik ile oluşturulmuştur: `FastDP`, `SlowerDP`ve `SlowestDP`.</span><span class="sxs-lookup"><span data-stu-id="79041-108">To demonstrate how <xref:System.Windows.Data.PriorityBinding> works, the `AsyncDataSource` object has been created with the following three properties: `FastDP`, `SlowerDP`, and `SlowestDP`.</span></span>  
  
 <span data-ttu-id="79041-109">`FastDP` get erişimcisi `_fastDP` veri üyesinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="79041-109">The get accessor of `FastDP` returns the value of the `_fastDP` data member.</span></span>  
  
 <span data-ttu-id="79041-110">`SlowerDP` get erişimcisi `_slowerDP` veri üyesinin değerini döndürmeden önce 3 saniye bekler.</span><span class="sxs-lookup"><span data-stu-id="79041-110">The get accessor of `SlowerDP` waits for 3 seconds before returning the value of the `_slowerDP` data member.</span></span>  
  
 <span data-ttu-id="79041-111">`SlowestDP` get erişimcisi `_slowestDP` veri üyesinin değerini döndürmeden önce 5 saniye bekler.</span><span class="sxs-lookup"><span data-stu-id="79041-111">The get accessor of `SlowestDP` waits for 5 seconds before returning the value of the `_slowestDP` data member.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79041-112">Bu örnek yalnızca tanıtım amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="79041-112">This example is for demonstration purposes only.</span></span> <span data-ttu-id="79041-113">.NET yönergeleri, bir alan kümesinden daha yavaş büyüklüğü olan özellikleri tanımlamaya karşı önerilir.</span><span class="sxs-lookup"><span data-stu-id="79041-113">The .NET guidelines recommend against defining properties that are orders of magnitude slower than a field set would be.</span></span> <span data-ttu-id="79041-114">Daha fazla bilgi için bkz. [Özellikler ve yöntemler arasında seçim yapma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="79041-114">For more information, see [Choosing Between Properties and Methods](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229054(v=vs.100)).</span></span>  
  
 [!code-csharp[PriorityBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <span data-ttu-id="79041-115"><xref:System.Windows.Controls.TextBlock.Text%2A> özelliği, <xref:System.Windows.Data.PriorityBinding>kullanarak yukarıdaki `AsyncDS` bağlar:</span><span class="sxs-lookup"><span data-stu-id="79041-115">The <xref:System.Windows.Controls.TextBlock.Text%2A> property binds to the above `AsyncDS` using <xref:System.Windows.Data.PriorityBinding>:</span></span>  
  
 [!code-xaml[PriorityBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="79041-116">Bağlama altyapısı <xref:System.Windows.Data.Binding> nesnelerini işlediğinde, `SlowestDP` özelliğine bağlantılı olan ilk <xref:System.Windows.Data.Binding>başlar.</span><span class="sxs-lookup"><span data-stu-id="79041-116">When the binding engine processes the <xref:System.Windows.Data.Binding> objects, it starts with the first <xref:System.Windows.Data.Binding>, which is bound to the `SlowestDP` property.</span></span> <span data-ttu-id="79041-117">Bu <xref:System.Windows.Data.Binding> işlendiğinde, 5 saniye boyunca uymadığı için bir değeri başarıyla döndürmez, bu nedenle sonraki <xref:System.Windows.Data.Binding> öğesi işlenir.</span><span class="sxs-lookup"><span data-stu-id="79041-117">When this <xref:System.Windows.Data.Binding> is processed, it does not return a value successfully because it is sleeping for 5 seconds, so the next <xref:System.Windows.Data.Binding> element is processed.</span></span> <span data-ttu-id="79041-118">Sonraki <xref:System.Windows.Data.Binding>, 3 saniye boyunca uyduğundan bir değeri başarıyla döndürmez.</span><span class="sxs-lookup"><span data-stu-id="79041-118">The next <xref:System.Windows.Data.Binding> does not return a value successfully because it is sleeping for 3 seconds.</span></span> <span data-ttu-id="79041-119">Bağlama altyapısı daha sonra `FastDP` özelliğine bağlantılı olan bir sonraki <xref:System.Windows.Data.Binding> öğesi üzerine gider.</span><span class="sxs-lookup"><span data-stu-id="79041-119">The binding engine then moves onto the next <xref:System.Windows.Data.Binding> element, which is bound to the `FastDP` property.</span></span> <span data-ttu-id="79041-120">Bu <xref:System.Windows.Data.Binding> "hızlı değer" değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="79041-120">This <xref:System.Windows.Data.Binding> returns the value "Fast Value".</span></span> <span data-ttu-id="79041-121"><xref:System.Windows.Controls.TextBlock> artık "Fast Value" değerini görüntülüyor.</span><span class="sxs-lookup"><span data-stu-id="79041-121">The <xref:System.Windows.Controls.TextBlock> now displays the value "Fast Value".</span></span>  
  
 <span data-ttu-id="79041-122">3 saniye geçtikten sonra, `SlowerDP` özelliği "daha yavaş değer" değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="79041-122">After 3 seconds elapses, the `SlowerDP` property returns the value "Slower Value".</span></span> <span data-ttu-id="79041-123"><xref:System.Windows.Controls.TextBlock> daha sonra "daha yavaş değer" değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="79041-123">The <xref:System.Windows.Controls.TextBlock> then displays the value "Slower Value".</span></span>  
  
 <span data-ttu-id="79041-124">5 saniye geçtikten sonra, `SlowestDP` özelliği "en yavaş değer" değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="79041-124">After 5 seconds elapses, the `SlowestDP` property returns the value "Slowest Value".</span></span> <span data-ttu-id="79041-125">İlk olarak listelenen bu bağlama en yüksek önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="79041-125">That binding has the highest priority because it is listed first.</span></span> <span data-ttu-id="79041-126"><xref:System.Windows.Controls.TextBlock> artık "en yavaş değer" değerini görüntülüyor.</span><span class="sxs-lookup"><span data-stu-id="79041-126">The <xref:System.Windows.Controls.TextBlock> now displays the value "Slowest Value".</span></span>  
  
 <span data-ttu-id="79041-127">Bir bağlamadan başarılı bir dönüş değeri olarak kabul edilen özellikler hakkında bilgi için bkz. <xref:System.Windows.Data.PriorityBinding>.</span><span class="sxs-lookup"><span data-stu-id="79041-127">See <xref:System.Windows.Data.PriorityBinding> for information about what is considered a successful return value from a binding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79041-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79041-128">See also</span></span>

- <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>
- [<span data-ttu-id="79041-129">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="79041-129">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="79041-130">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="79041-130">How-to Topics</span></span>](data-binding-how-to-topics.md)
