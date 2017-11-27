---
title: "Nasıl yapılır: Metin Süslemesi Oluşturma"
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9229ce86dbe640c4eb960c455dd049ff40b38d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="98683-102">Nasıl yapılır: Metin Süslemesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="98683-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="98683-103">A <xref:System.Windows.TextDecoration> metne ekleyebileceğiniz görsel süslemedir nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="98683-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="98683-104">Metin düzenlemelerinin dört tür vardır: alt çizgi, taban çizgisi, üst çizgi ve üst çizgi.</span><span class="sxs-lookup"><span data-stu-id="98683-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="98683-105">Aşağıdaki örnek metin göre metin düzenlemelerinin konumlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98683-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 <span data-ttu-id="98683-106">![Metin dekorasyonu konumları diyagramı](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span><span class="sxs-lookup"><span data-stu-id="98683-106">![Diagram of text decoration locations](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span></span>  
<span data-ttu-id="98683-107">Metin dekorasyonu türleri örneği</span><span class="sxs-lookup"><span data-stu-id="98683-107">Example of text decoration types</span></span>  
  
 <span data-ttu-id="98683-108">Metin dekorasyonu metne eklemek için oluşturma bir <xref:System.Windows.TextDecoration> nesne ve özelliklerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="98683-108">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="98683-109">Kullanım <xref:System.Windows.TextDecoration.Location%2A> özelliği dekorasyonu, alt çizgi gibi göründüğü belirtin.</span><span class="sxs-lookup"><span data-stu-id="98683-109">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="98683-110">Kullanım <xref:System.Windows.TextDecoration.Pen%2A> düz dolgu veya gradyan rengi gibi dekorasyonu görünümünü belirtmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="98683-110">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="98683-111">İçin bir değer belirtmezseniz, <xref:System.Windows.TextDecoration.Pen%2A> özelliği, aynı renk metin olarak varsayılır.</span><span class="sxs-lookup"><span data-stu-id="98683-111">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="98683-112">Tanımladığınız sonra bir <xref:System.Windows.TextDecoration> nesne, ekleyin <xref:System.Windows.TextDecorations> istenen metin nesnesi koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="98683-112">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="98683-113">Aşağıdaki örnek, doğrusal gradyan fırçası ve kesikli kalem ile biçimlendirilmiş bir metin dekorasyonu gösterir.</span><span class="sxs-lookup"><span data-stu-id="98683-113">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 <span data-ttu-id="98683-114">![Metin dekorasyonu doğrusal gradyan alt çizgiyle](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span><span class="sxs-lookup"><span data-stu-id="98683-114">![Text decoration with linear gradient underline](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span></span>  
<span data-ttu-id="98683-115">Bir alt çizgi örneği stilde ile doğrusal gradyan fırçası ve kesikli kalem</span><span class="sxs-lookup"><span data-stu-id="98683-115">Example of an underline styled with a linear gradient brush and dashed pen</span></span>  
  
 <span data-ttu-id="98683-116"><xref:System.Windows.Documents.Hyperlink> Nesnesidir köprüler akış içeriği barındırmanıza olanak tanıyan bir satır içi düzeyde akış içeriği öğesidir.</span><span class="sxs-lookup"><span data-stu-id="98683-116">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="98683-117">Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="98683-117">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="98683-118"><xref:System.Windows.TextDecoration>nesneleri, performans örneği oluşturmak için yoğun olabilir, özellikle birçok varsa <xref:System.Windows.Documents.Hyperlink> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="98683-118"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="98683-119">Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri, bir alt çizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.</span><span class="sxs-lookup"><span data-stu-id="98683-119">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="98683-120">Aşağıdaki örnekte, altı çizili "My MSN" bağlantısı için dinamik — yalnızca zaman göründüğü <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="98683-120">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="98683-121">![TextDecorations görüntüleyen köprüler](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="98683-121">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="98683-122">TextDecorations ile tanımlanan köprüler</span><span class="sxs-lookup"><span data-stu-id="98683-122">Hyperlinks defined with TextDecorations</span></span>  
  
 <span data-ttu-id="98683-123">Daha fazla bilgi için bkz: [belirtin olup olmadığını bir köprü çizilir](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="98683-123">For more information, see [Specify Whether a Hyperlink is Underlined](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98683-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="98683-124">Example</span></span>  
 <span data-ttu-id="98683-125">Aşağıdaki kod örneğinde bir alt çizgi dekorasyonu varsayılan yazı tipi değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="98683-125">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="98683-126">Aşağıdaki kod örneğinde, altı çizili metin düzenleme kalem için düz renk fırça ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="98683-126">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="98683-127">Aşağıdaki kod örneğinde, altı çizili metin düzenleme kesik kalem için doğrusal gradyan fırçası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="98683-127">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="98683-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98683-128">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="98683-129">Olup olmadığını bir köprü altı çizili belirtin</span><span class="sxs-lookup"><span data-stu-id="98683-129">Specify Whether a Hyperlink is Underlined</span></span>](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
