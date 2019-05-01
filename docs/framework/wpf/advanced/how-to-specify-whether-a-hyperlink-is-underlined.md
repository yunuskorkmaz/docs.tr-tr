---
title: 'Nasıl yapılır: Köprünün Altı Çizili Olup Olmadığını Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 5718912e24a0697f209669b0ab4e7f4df1765ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943955"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="82b9d-102">Nasıl yapılır: Köprünün Altı Çizili Olup Olmadığını Belirtme</span><span class="sxs-lookup"><span data-stu-id="82b9d-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="82b9d-103"><xref:System.Windows.Documents.Hyperlink> Köprüler akış içeriği barındırmanıza olanak tanır bir satır içi düzeydeki akış içerik öğesi nesnedir.</span><span class="sxs-lookup"><span data-stu-id="82b9d-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="82b9d-104">Varsayılan olarak, <xref:System.Windows.Documents.Hyperlink> kullanan bir <xref:System.Windows.TextDecoration> altı çizili görüntülenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="82b9d-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="82b9d-105"><xref:System.Windows.TextDecoration> nesneleri oluşturmak için yoğun performans olabilir, özellikle Çoğu varsa <xref:System.Windows.Documents.Hyperlink> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="82b9d-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="82b9d-106">Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri altçizgi gibi yalnızca bir olay tetiklendiğinde gösteren düşünmek isteyebilirsiniz <xref:System.Windows.ContentElement.MouseEnter> olay.</span><span class="sxs-lookup"><span data-stu-id="82b9d-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="82b9d-107">Aşağıdaki örnekte, "My MSN" bağlantısını için altı çizili dinamik ise, diğer bir deyişle, yalnızca zaman göründüğü <xref:System.Windows.ContentElement.MouseEnter> olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="82b9d-107">In the following example, the underline for the "My MSN" link is dynamic, that is, it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
  ![Köprüler TextDecorations görüntüleme](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)  

## <a name="example"></a><span data-ttu-id="82b9d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="82b9d-109">Example</span></span>  
 <span data-ttu-id="82b9d-110">Aşağıdaki biçimlendirme örnek gösterildiği bir <xref:System.Windows.Documents.Hyperlink> ve alt çizgi olmadan tanımlanan:</span><span class="sxs-lookup"><span data-stu-id="82b9d-110">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="82b9d-111">Aşağıdaki kod örneği için altı çizili oluşturma işlemi gösterilmektedir <xref:System.Windows.Documents.Hyperlink> üzerinde <xref:System.Windows.ContentElement.MouseEnter> olay ve kaldırılacağını <xref:System.Windows.ContentElement.MouseLeave> olay.</span><span class="sxs-lookup"><span data-stu-id="82b9d-111">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="82b9d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82b9d-112">See also</span></span>

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="82b9d-113">WPF Uygulama Performansını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="82b9d-113">Optimizing WPF Application Performance</span></span>](optimizing-wpf-application-performance.md)
- [<span data-ttu-id="82b9d-114">Metin Süslemesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="82b9d-114">Create a Text Decoration</span></span>](how-to-create-a-text-decoration.md)
