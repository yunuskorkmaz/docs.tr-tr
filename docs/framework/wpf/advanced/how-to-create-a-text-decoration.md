---
title: 'Nasıl yapılır: Metin Süslemesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185931"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="b74f3-102">Nasıl yapılır: Metin Süslemesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b74f3-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="b74f3-103"><xref:System.Windows.TextDecoration> Nesne, metne ekleyebileceğiniz görsel bir süslemedir.</span><span class="sxs-lookup"><span data-stu-id="b74f3-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="b74f3-104">Dört tür metin süslemesi vardır: altı çizili, temel, vurucu ve üst çizgi.</span><span class="sxs-lookup"><span data-stu-id="b74f3-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="b74f3-105">Aşağıdaki örnek, metin süslemelerinin metne göre konumlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b74f3-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 ![Metin süsleme türleri diyagramı](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 <span data-ttu-id="b74f3-107">Metne metin süslemesi eklemek <xref:System.Windows.TextDecoration> için bir nesne oluşturun ve özelliklerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b74f3-107">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="b74f3-108">Metin <xref:System.Windows.TextDecoration.Location%2A> süslemesinin altı çizili gibi nerede göründüğünü belirtmek için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b74f3-108">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="b74f3-109">Metin <xref:System.Windows.TextDecoration.Pen%2A> süslemesinin görünümünü belirtmek için katı dolgu veya degrade renk gibi özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b74f3-109">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="b74f3-110"><xref:System.Windows.TextDecoration.Pen%2A> Özellik için bir değer belirtmezseniz, süslemeler varsayılan olarak metinle aynı renge ayrılır.</span><span class="sxs-lookup"><span data-stu-id="b74f3-110">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="b74f3-111">Bir <xref:System.Windows.TextDecoration> nesneyi tanımladıktan sonra, <xref:System.Windows.TextDecorations> nesneyi istenen metin nesnesinin koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b74f3-111">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="b74f3-112">Aşağıdaki örnek, doğrusal degrade fırçası ve kesikli kalemle stile sahip bir metin süslemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b74f3-112">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 ![Doğrusal degrade altı çizili metin süslemesi](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <span data-ttu-id="b74f3-114">Nesne, <xref:System.Windows.Documents.Hyperlink> akış içeriği içinde köprüler barındırmanızı sağlayan bir satır içi düzey akış içeriği öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b74f3-114">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="b74f3-115">Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.TextDecoration> bir alt çizgi yi görüntülemek için bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="b74f3-115">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="b74f3-116"><xref:System.Windows.TextDecoration>nesneler, özellikle çok sayıda <xref:System.Windows.Documents.Hyperlink> nesne varsa, anlık olarak performans yoğun olabilir.</span><span class="sxs-lookup"><span data-stu-id="b74f3-116"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="b74f3-117"><xref:System.Windows.Documents.Hyperlink> Öğeleri kapsamlı bir şekilde kullanırsanız, yalnızca olay gibi bir olayı tetiklerken <xref:System.Windows.ContentElement.MouseEnter> altı çiziyi göstermeyi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b74f3-117">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="b74f3-118">Aşağıdaki örnekte, "MSN' mevzum" bağlantısının alt çizgi <xref:System.Windows.ContentElement.MouseEnter> altı dinamiktir ve yalnızca olay tetiklendiğinde görünür.</span><span class="sxs-lookup"><span data-stu-id="b74f3-118">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 ![TextDecorations görüntüleyen köprüler](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 <span data-ttu-id="b74f3-120">Daha fazla bilgi için [bkz.](how-to-specify-whether-a-hyperlink-is-underlined.md)</span><span class="sxs-lookup"><span data-stu-id="b74f3-120">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b74f3-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b74f3-121">Example</span></span>  
 <span data-ttu-id="b74f3-122">Aşağıdaki kod örneğinde, altı çizili metin süslemesi varsayılan yazı tipi değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b74f3-122">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="b74f3-123">Aşağıdaki kod örneğinde, kalem için düz renkli bir fırça ile altı çizili metin süslemesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b74f3-123">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="b74f3-124">Aşağıdaki kod örneğinde, kesikli kalem için doğrusal degrade fırçası ile altı çizili metin süslemesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b74f3-124">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="b74f3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b74f3-125">See also</span></span>

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="b74f3-126">Köprünün Altı Çizili Olup Olmadığını Belirtme</span><span class="sxs-lookup"><span data-stu-id="b74f3-126">Specify Whether a Hyperlink is Underlined</span></span>](how-to-specify-whether-a-hyperlink-is-underlined.md)
