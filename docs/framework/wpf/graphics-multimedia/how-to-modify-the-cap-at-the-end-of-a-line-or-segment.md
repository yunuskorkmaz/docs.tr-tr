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
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme
Bu örnekte, açık bir <xref:System.Windows.Shapes.Shape> öğesinin başlangıcında veya sonunda şeklinin nasıl değiştirileceği gösterilmektedir. Açık bir <xref:System.Windows.Shapes.Shape>başındaki ucu değiştirmek için, <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> özelliğini kullanın. Açık bir <xref:System.Windows.Shapes.Shape>sonundaki ucu değiştirmek için, <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> özelliğini kullanın. Kullanılabilir çizgi Cap 'leri görüntülemek için <xref:System.Windows.Media.PenLineCap> sabit listesine bakın.  
  
> [!NOTE]
> Bu özellik yalnızca <xref:System.Windows.Shapes.Line>, bir <xref:System.Windows.Shapes.Polyline>veya açık bir <xref:System.Windows.Shapes.Path> öğesi gibi bir açık şekli etkiler.  
  
 Aşağıdaki örnek dört <xref:System.Windows.Shapes.Polyline> öğesi çizer ve her birinin sonunda farklı bir şekil kümesi kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
