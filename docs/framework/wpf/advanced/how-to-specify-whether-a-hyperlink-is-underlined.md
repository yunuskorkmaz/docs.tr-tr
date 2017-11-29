---
title: "Nasıl yapılır: Köprünün Altı Çizili Olup Olmadığını Belirtme"
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
helpviewer_keywords: Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7914b3b3332b7ea0abe05b3048b5016888e2d93e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="b98bc-102">Nasıl yapılır: Köprünün Altı Çizili Olup Olmadığını Belirtme</span><span class="sxs-lookup"><span data-stu-id="b98bc-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="b98bc-103"><xref:System.Windows.Documents.Hyperlink> Nesnesidir köprüler akış içeriği barındırmanıza olanak tanıyan bir satır içi düzeyde akış içeriği öğesidir.</span><span class="sxs-lookup"><span data-stu-id="b98bc-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="b98bc-104">Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="b98bc-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="b98bc-105"><xref:System.Windows.TextDecoration>nesneleri, performans örneği oluşturmak için yoğun olabilir, özellikle birçok varsa <xref:System.Windows.Documents.Hyperlink> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b98bc-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="b98bc-106">Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri, bir alt çizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.</span><span class="sxs-lookup"><span data-stu-id="b98bc-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="b98bc-107">Aşağıdaki örnekte, altı çizili "My MSN" bağlantısı için dinamik — yalnızca zaman göründüğü <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="b98bc-107">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="b98bc-108">![TextDecorations görüntüleyen köprüler](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="b98bc-108">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="b98bc-109">TextDecorations ile tanımlanan köprüler</span><span class="sxs-lookup"><span data-stu-id="b98bc-109">Hyperlinks defined with TextDecorations</span></span>  
  
## <a name="example"></a><span data-ttu-id="b98bc-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b98bc-110">Example</span></span>  
 <span data-ttu-id="b98bc-111">Aşağıdaki biçimlendirme örnek gösterildiği bir <xref:System.Windows.Documents.Hyperlink> ile ve bir alt çizginin olmadan tanımlanan:</span><span class="sxs-lookup"><span data-stu-id="b98bc-111">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="b98bc-112">Aşağıdaki kod örneği için bir alt çizginin oluşturulacağını gösterir <xref:System.Windows.Documents.Hyperlink> üzerinde <xref:System.Windows.ContentElement.MouseEnter> olayı ve kaldırılacağını <xref:System.Windows.ContentElement.MouseLeave> olay.</span><span class="sxs-lookup"><span data-stu-id="b98bc-112">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="b98bc-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b98bc-113">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="b98bc-114">WPF Uygulama performansı en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="b98bc-114">Optimizing WPF Application Performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [<span data-ttu-id="b98bc-115">Metin dekorasyonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="b98bc-115">Create a Text Decoration</span></span>](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
