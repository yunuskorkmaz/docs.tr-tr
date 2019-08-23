---
title: 'Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: 53487417636dae8d855fe70b7b9255351a2dfb1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916128"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme
Bu örnek, bir açık <xref:System.Windows.Shapes.Shape> öğenin başlangıcında veya sonunda şeklinin nasıl değiştirileceğini gösterir. Bir açık <xref:System.Windows.Shapes.Shape>öğenin başındaki ucu değiştirmek için, <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> özelliğini kullanın. Bir açık <xref:System.Windows.Shapes.Shape>öğenin sonundaki ucu değiştirmek için, <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> özelliğini kullanın. Kullanılabilir çizgi Cap 'leri görüntülemek için bkz <xref:System.Windows.Media.PenLineCap> . sabit listesi.  
  
> [!NOTE]
> Bu özellik yalnızca <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Polyline>,, ya da açık <xref:System.Windows.Shapes.Path> bir öğe gibi açık bir şekli etkiler.  
  
 Aşağıdaki örnek dört <xref:System.Windows.Shapes.Polyline> öğe çizer ve her birinin sonunda farklı bir şekil kümesi kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Bu örnek, daha büyük bir örneğin bir parçasıdır; Tüm örnek için bkz. [Şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
