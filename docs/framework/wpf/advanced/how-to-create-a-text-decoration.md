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
ms.openlocfilehash: b85bbaed13d9406f85c62a9a5bc5ca220d90b0b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607953"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="f15db-102">Nasıl yapılır: Metin Süslemesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f15db-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="f15db-103">A <xref:System.Windows.TextDecoration> metni ekleyebileceğiniz görsel bir süsleme nesnedir.</span><span class="sxs-lookup"><span data-stu-id="f15db-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="f15db-104">Metin süslemeleri dört tür vardır: alt çizgi, temel, üstü çizili ve üst çizgi.</span><span class="sxs-lookup"><span data-stu-id="f15db-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="f15db-105">Aşağıdaki örnek, metin düzenlemelerinin metin göreli konumlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f15db-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 <span data-ttu-id="f15db-106">![Metin süslemesi konumları diyagramı](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span><span class="sxs-lookup"><span data-stu-id="f15db-106">![Diagram of text decoration locations](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span></span>  
<span data-ttu-id="f15db-107">Metin süslemesi türleri örneği</span><span class="sxs-lookup"><span data-stu-id="f15db-107">Example of text decoration types</span></span>  
  
 <span data-ttu-id="f15db-108">Metin süslemesi metin eklemek için oluşturun bir <xref:System.Windows.TextDecoration> nesne ve özelliklerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f15db-108">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="f15db-109">Kullanım <xref:System.Windows.TextDecoration.Location%2A> metin düzenleme, alt çizgi gibi görüneceği yeri belirtmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="f15db-109">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="f15db-110">Kullanım <xref:System.Windows.TextDecoration.Pen%2A> tek renk dolgu veya gradyan rengi gibi metin düzenleme görünümünü belirtmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="f15db-110">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="f15db-111">İçin bir değer belirtmezseniz <xref:System.Windows.TextDecoration.Pen%2A> özelliğini aynı metin rengini varsayılır.</span><span class="sxs-lookup"><span data-stu-id="f15db-111">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="f15db-112">Tanımladığınız sonra bir <xref:System.Windows.TextDecoration> nesne, ekleyin <xref:System.Windows.TextDecorations> istenen metin nesnesi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f15db-112">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="f15db-113">Aşağıdaki örnek, doğrusal gradyan fırçası ve bir kesikli kalem ile biçimlendirilmiş metin süslemesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f15db-113">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 <span data-ttu-id="f15db-114">![Doğrusal gradyan altı çizili metin süslemesi](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span><span class="sxs-lookup"><span data-stu-id="f15db-114">![Text decoration with linear gradient underline](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span></span>  
<span data-ttu-id="f15db-115">Doğrusal gradyan ile bir alt çizgi örneği biçimlendirilmiş ve kesikli kalem</span><span class="sxs-lookup"><span data-stu-id="f15db-115">Example of an underline styled with a linear gradient brush and dashed pen</span></span>  
  
 <span data-ttu-id="f15db-116"><xref:System.Windows.Documents.Hyperlink> Köprüler akış içeriği barındırmanıza olanak tanır bir satır içi düzeydeki akış içerik öğesi nesnedir.</span><span class="sxs-lookup"><span data-stu-id="f15db-116">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="f15db-117">Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="f15db-117">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="f15db-118"><xref:System.Windows.TextDecoration> nesneleri oluşturmak için yoğun performans olabilir, özellikle Çoğu varsa <xref:System.Windows.Documents.Hyperlink> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f15db-118"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="f15db-119">Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri altçizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.</span><span class="sxs-lookup"><span data-stu-id="f15db-119">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="f15db-120">Aşağıdaki örnekte, "My MSN" bağlantısını için altı çizili dinamik — zaman görünür <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="f15db-120">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="f15db-121">![TextDecorations görüntüleyen köprüler](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="f15db-121">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="f15db-122">TextDecorations ile tanımlanan köprüler</span><span class="sxs-lookup"><span data-stu-id="f15db-122">Hyperlinks defined with TextDecorations</span></span>  
  
 <span data-ttu-id="f15db-123">Daha fazla bilgi için [belirtin olmadığını köprünün altı çizilir](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="f15db-123">For more information, see [Specify Whether a Hyperlink is Underlined](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f15db-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f15db-124">Example</span></span>  
 <span data-ttu-id="f15db-125">Aşağıdaki kod örneğinde altı çizili metin düzenleme varsayılan yazı tipi değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f15db-125">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="f15db-126">Aşağıdaki kod örneğinde tek renk Fırçası kalem için altı çizili metin düzenleme oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f15db-126">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="f15db-127">Aşağıdaki kod örneğinde altı çizili metin düzenleme doğrusal gradyan fırçası kesik kalem için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f15db-127">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="f15db-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f15db-128">See also</span></span>
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="f15db-129">Köprünün Altı Çizili Olup Olmadığını Belirtme</span><span class="sxs-lookup"><span data-stu-id="f15db-129">Specify Whether a Hyperlink is Underlined</span></span>](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
