---
title: 'Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 5f755d7b4d1682755ea461121f91c0666d450ad1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452785"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a><span data-ttu-id="93ba2-102">Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme</span><span class="sxs-lookup"><span data-stu-id="93ba2-102">How to: Modify the Cap at the End of a Line or Segment</span></span>
<span data-ttu-id="93ba2-103">Bu örnekte, açık bir <xref:System.Windows.Shapes.Shape> öğesinin başlangıcında veya sonunda şeklinin nasıl değiştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="93ba2-103">This example shows how to modify the shape at the start or end of an open <xref:System.Windows.Shapes.Shape> element.</span></span> <span data-ttu-id="93ba2-104">Açık bir <xref:System.Windows.Shapes.Shape>başındaki ucu değiştirmek için, <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="93ba2-104">To change the cap at the beginning of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> property.</span></span> <span data-ttu-id="93ba2-105">Açık bir <xref:System.Windows.Shapes.Shape>sonundaki ucu değiştirmek için, <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="93ba2-105">To change the cap at the end of an open <xref:System.Windows.Shapes.Shape>, use its <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> property.</span></span> <span data-ttu-id="93ba2-106">Kullanılabilir çizgi Cap 'leri görüntülemek için <xref:System.Windows.Media.PenLineCap> sabit listesine bakın.</span><span class="sxs-lookup"><span data-stu-id="93ba2-106">To view the available line caps, see the <xref:System.Windows.Media.PenLineCap> enumeration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93ba2-107">Bu özellik yalnızca <xref:System.Windows.Shapes.Line>, bir <xref:System.Windows.Shapes.Polyline>veya açık bir <xref:System.Windows.Shapes.Path> öğesi gibi bir açık şekli etkiler.</span><span class="sxs-lookup"><span data-stu-id="93ba2-107">This property only affects an open shape, such as a <xref:System.Windows.Shapes.Line>, a <xref:System.Windows.Shapes.Polyline>, or an open <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 <span data-ttu-id="93ba2-108">Aşağıdaki örnek dört <xref:System.Windows.Shapes.Polyline> öğesi çizer ve her birinin sonunda farklı bir şekil kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="93ba2-108">The following example draws four <xref:System.Windows.Shapes.Polyline> elements and uses a different set of shapes on the ends of each.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93ba2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="93ba2-109">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 <span data-ttu-id="93ba2-110">Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="93ba2-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ba2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93ba2-111">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
