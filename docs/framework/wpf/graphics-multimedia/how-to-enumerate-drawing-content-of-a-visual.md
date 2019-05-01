---
title: 'Nasıl yapılır: Görselin Çizim İçeriğini Numaralandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 4f0afc1075fe66c7f154fcef3cd883709db55316
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947478"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="6bab8-102">Nasıl yapılır: Görselin Çizim İçeriğini Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="6bab8-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="6bab8-103"><xref:System.Windows.Media.Drawing> Nesne içeriğini numaralandırma için nesne modeli sağlar bir <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="6bab8-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bab8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6bab8-104">Example</span></span>  
 <span data-ttu-id="6bab8-105">Aşağıdaki örnekte <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> alınacak yöntemi <xref:System.Windows.Media.DrawingGroup> değerini bir <xref:System.Windows.Media.Visual> ve onu numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="6bab8-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bab8-106">Görselin içeriklerini sıralanırken alınırken <xref:System.Windows.Media.Drawing> nesneleri ve vektör grafik yönerge listesi olarak işleme verileri temel alınan gösterimini değil.</span><span class="sxs-lookup"><span data-stu-id="6bab8-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="6bab8-107">Daha fazla bilgi için [WPF Grafik işlemeye genel bakış](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6bab8-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="6bab8-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bab8-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="6bab8-109">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6bab8-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="6bab8-110">WPF Grafik İşlemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6bab8-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
