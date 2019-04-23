---
title: 'Nasıl yapılır: Çizgi Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: c11dfb9523834ec2e622cb2e62bd6982a1a78fd4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143526"
---
# <a name="how-to-draw-a-line"></a><span data-ttu-id="ccfcf-102">Nasıl yapılır: Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="ccfcf-102">How to: Draw a Line</span></span>
<span data-ttu-id="ccfcf-103">Bu örnekte kullanarak çizgi çizmek gösterilmektedir <xref:System.Windows.Shapes.Line> öğesi.</span><span class="sxs-lookup"><span data-stu-id="ccfcf-103">This example shows you how to draw lines by using the <xref:System.Windows.Shapes.Line> element.</span></span>  
  
 <span data-ttu-id="ccfcf-104">Bir çizgi çizmek için oluşturma bir <xref:System.Windows.Shapes.Line> öğesi.</span><span class="sxs-lookup"><span data-stu-id="ccfcf-104">To draw a line, create a <xref:System.Windows.Shapes.Line> element.</span></span> <span data-ttu-id="ccfcf-105">Kullanın, <xref:System.Windows.Shapes.Line.X1%2A> ve <xref:System.Windows.Shapes.Line.Y1%2A> özellikleri, başlangıç noktası; ve kullanmak için kendi <xref:System.Windows.Shapes.Line.X2%2A> ve <xref:System.Windows.Shapes.Line.Y2%2A> uç noktasına ayarlamak için özellikler.</span><span class="sxs-lookup"><span data-stu-id="ccfcf-105">Use its <xref:System.Windows.Shapes.Line.X1%2A> and <xref:System.Windows.Shapes.Line.Y1%2A> properties to set its start point; and use its <xref:System.Windows.Shapes.Line.X2%2A> and <xref:System.Windows.Shapes.Line.Y2%2A> properties to set its end point.</span></span> <span data-ttu-id="ccfcf-106">Son olarak ayarlayın, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> çünkü bir çizgi görünmez.</span><span class="sxs-lookup"><span data-stu-id="ccfcf-106">Finally, set its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> because a line without a stroke is invisible.</span></span>  
  
 <span data-ttu-id="ccfcf-107">Ayar <xref:System.Windows.Shapes.Shape.Fill%2A> öğesi bir satır için hiçbir iç çizginin olmadığı için hiçbir etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ccfcf-107">Setting the <xref:System.Windows.Shapes.Shape.Fill%2A> element for a line has no effect, because a line has no interior.</span></span>  
  
 <span data-ttu-id="ccfcf-108">Aşağıdaki örnek üç satır içinde çizen bir <xref:System.Windows.Controls.Canvas> öğesi.</span><span class="sxs-lookup"><span data-stu-id="ccfcf-108">The following example draws three lines inside a <xref:System.Windows.Controls.Canvas> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccfcf-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ccfcf-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 <span data-ttu-id="ccfcf-110">Bu örnek, daha büyük bir örnek bir parçasıdır; tam bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="ccfcf-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccfcf-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccfcf-111">See also</span></span>

- <xref:System.Windows.Shapes.Line>
- [<span data-ttu-id="ccfcf-112">Şekil öğeleri örneği</span><span class="sxs-lookup"><span data-stu-id="ccfcf-112">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
