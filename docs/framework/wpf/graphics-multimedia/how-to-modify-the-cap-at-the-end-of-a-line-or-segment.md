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
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme
Bu örnekte, başında veya açık sonuna şeklini değiştirmek gösterilmektedir <xref:System.Windows.Shapes.Shape> öğesi. Cap açık başındaki değiştirmek için <xref:System.Windows.Shapes.Shape>, kullanma, <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> özelliği. Cap açık sonunda değiştirmek için <xref:System.Windows.Shapes.Shape>, kullanma, <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> özelliği. Kullanılabilir satır caps görüntülemek için bkz: <xref:System.Windows.Media.PenLineCap> sabit listesi.  
  
> [!NOTE]
>  Bu özellik yalnızca açık bir şekli gibi etkiler bir <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>, ya da açık <xref:System.Windows.Shapes.Path> öğesi.  
  
 Aşağıdaki örnekte, dört çizer <xref:System.Windows.Shapes.Polyline> öğeleri ve her birinin uçlarında farklı bir şekil kümesi kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Bu örnek, daha büyük bir örnek bir parçasıdır; tam bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
