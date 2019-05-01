---
title: 'Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 462e32520393a1c23809cce8eb3c130c13bc882f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947270"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="5e6c9-102">Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme</span><span class="sxs-lookup"><span data-stu-id="5e6c9-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="5e6c9-103">Bu örnekte, başında veya açık sonuna şeklini değiştirmek gösterilmektedir <xref:System.Windows.Shapes.Shape> öğesi.</span><span class="sxs-lookup"><span data-stu-id="5e6c9-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="5e6c9-104">Cap açık başındaki değiştirmek için <xref:System.Windows.Shapes.Shape>, kullanma, <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5e6c9-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="5e6c9-105">Cap açık sonunda değiştirmek için <xref:System.Windows.Shapes.Shape>, kullanma, <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5e6c9-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="5e6c9-106">Kullanılabilir satır caps görüntülemek için bkz: <xref:System.Windows.Media.PenLineCap> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="5e6c9-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e6c9-107">Bu özellik yalnızca açık bir şekli gibi etkiler bir <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>, ya da açık <xref:System.Windows.Shapes.Path> öğesi.</span><span class="sxs-lookup"><span data-stu-id="5e6c9-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="5e6c9-108">Aşağıdaki örnekte, dört çizer <xref:System.Windows.Shapes.Polyline> öğeleri ve her birinin uçlarında farklı bir şekil kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e6c9-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e6c9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e6c9-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="5e6c9-110">Bu örnek, daha büyük bir örnek bir parçasıdır; tam bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="5e6c9-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e6c9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e6c9-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
