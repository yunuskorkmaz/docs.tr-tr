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
ms.openlocfilehash: d586eef8d1308070da38a0a54c63c3ba64d30c8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133841"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="14286-102">Nasıl yapılır: Metin Süslemesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="14286-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="14286-103">A <xref:System.Windows.TextDecoration> metni ekleyebileceğiniz görsel bir süsleme nesnedir.</span><span class="sxs-lookup"><span data-stu-id="14286-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="14286-104">Metin süslemeleri dört tür vardır: alt çizgi, temel, üstü çizili ve üst çizgi.</span><span class="sxs-lookup"><span data-stu-id="14286-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="14286-105">Aşağıdaki örnek, metin düzenlemelerinin metin göreli konumlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="14286-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 ![Metin düzenleme türleri diyagramı](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 <span data-ttu-id="14286-107">Metin süslemesi metin eklemek için oluşturun bir <xref:System.Windows.TextDecoration> nesne ve özelliklerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="14286-107">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="14286-108">Kullanım <xref:System.Windows.TextDecoration.Location%2A> metin düzenleme, alt çizgi gibi görüneceği yeri belirtmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="14286-108">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="14286-109">Kullanım <xref:System.Windows.TextDecoration.Pen%2A> tek renk dolgu veya gradyan rengi gibi metin düzenleme görünümünü belirtmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="14286-109">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="14286-110">İçin bir değer belirtmezseniz <xref:System.Windows.TextDecoration.Pen%2A> özelliğini aynı metin rengini varsayılır.</span><span class="sxs-lookup"><span data-stu-id="14286-110">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="14286-111">Tanımladığınız sonra bir <xref:System.Windows.TextDecoration> nesne, ekleyin <xref:System.Windows.TextDecorations> istenen metin nesnesi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="14286-111">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="14286-112">Aşağıdaki örnek, doğrusal gradyan fırçası ve bir kesikli kalem ile biçimlendirilmiş metin süslemesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="14286-112">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 ![Doğrusal gradyan altı çizili metin düzenleme](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <span data-ttu-id="14286-114"><xref:System.Windows.Documents.Hyperlink> Köprüler akış içeriği barındırmanıza olanak tanır bir satır içi düzeydeki akış içerik öğesi nesnedir.</span><span class="sxs-lookup"><span data-stu-id="14286-114">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="14286-115">Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="14286-115">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <xref:System.Windows.TextDecoration> <span data-ttu-id="14286-116">nesneleri oluşturmak için yoğun performans olabilir, özellikle Çoğu varsa <xref:System.Windows.Documents.Hyperlink> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="14286-116">objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="14286-117">Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri altçizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.</span><span class="sxs-lookup"><span data-stu-id="14286-117">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="14286-118">Aşağıdaki örnekte, "My MSN" bağlantısını için altı çizili dinamik — zaman görünür <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="14286-118">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 ![Köprüler TextDecorations görüntüleme](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  
   
 <span data-ttu-id="14286-120">Daha fazla bilgi için [belirtin olmadığını köprünün altı çizilir](how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="14286-120">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14286-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="14286-121">Example</span></span>  
 <span data-ttu-id="14286-122">Aşağıdaki kod örneğinde altı çizili metin düzenleme varsayılan yazı tipi değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="14286-122">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="14286-123">Aşağıdaki kod örneğinde tek renk Fırçası kalem için altı çizili metin düzenleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="14286-123">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="14286-124">Aşağıdaki kod örneğinde altı çizili metin düzenleme doğrusal gradyan fırçası kesik kalem için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="14286-124">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="14286-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14286-125">See also</span></span>

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="14286-126">Köprünün Altı Çizili Olup Olmadığını Belirtme</span><span class="sxs-lookup"><span data-stu-id="14286-126">Specify Whether a Hyperlink is Underlined</span></span>](how-to-specify-whether-a-hyperlink-is-underlined.md)
