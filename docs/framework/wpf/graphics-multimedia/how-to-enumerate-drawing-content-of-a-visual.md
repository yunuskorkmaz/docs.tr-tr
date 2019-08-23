---
title: 'Nasıl yapılır: Görselin Çizim İçeriğini Numaralandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930079"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="5ee39-102">Nasıl yapılır: Görselin Çizim İçeriğini Numaralandırma</span><span class="sxs-lookup"><span data-stu-id="5ee39-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="5ee39-103">Nesnesi, içeriğini <xref:System.Windows.Media.Visual>listelemek için bir nesne modeli sağlar. <xref:System.Windows.Media.Drawing></span><span class="sxs-lookup"><span data-stu-id="5ee39-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ee39-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ee39-104">Example</span></span>  
 <span data-ttu-id="5ee39-105">Aşağıdaki örnek, <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> <xref:System.Windows.Media.DrawingGroup> değerini <xref:System.Windows.Media.Visual> almak ve numaralandırmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ee39-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ee39-106">Görselin içeriğini Numaralandırdığınızda, nesneleri, işleme verilerinin bir vektör grafik <xref:System.Windows.Media.Drawing> yönerge listesi olarak değil, temel gösterimini değil, alıyor olursunuz.</span><span class="sxs-lookup"><span data-stu-id="5ee39-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="5ee39-107">Daha fazla bilgi için bkz. [WPF Grafik Işlemeye genel bakış](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5ee39-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="5ee39-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ee39-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="5ee39-109">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5ee39-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="5ee39-110">WPF Grafik İşlemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5ee39-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
