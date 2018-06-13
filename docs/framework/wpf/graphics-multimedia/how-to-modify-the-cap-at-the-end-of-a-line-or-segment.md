---
title: 'Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: e69f461d426fc6a587263cea7a18478da53b5b09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559843"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme
Bu örnek, başlangıç veya açık bir sonunda şeklinin nasıl değiştirileceğini gösterir <xref:System.Windows.Shapes.Shape> öğesi. Açık bir başındaki cap değiştirmek için <xref:System.Windows.Shapes.Shape>, kullanma, <xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> özelliği. Açık bir sonunda cap değiştirmek için <xref:System.Windows.Shapes.Shape>, kullanma, <xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> özelliği. Kullanılabilir satır caps görüntülemek için bkz: <xref:System.Windows.Media.PenLineCap> numaralandırması.  
  
> [!NOTE]
>  Bu özellik yalnızca açık bir şekli gibi etkiler bir <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Polyline>, veya açık bir <xref:System.Windows.Shapes.Path> öğesi.  
  
 Aşağıdaki örnek dört çizer <xref:System.Windows.Shapes.Polyline> öğeleri ve her birinin ucunun farklı bir şekil kümesi kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 Bu örnek daha büyük bir örneğin parçasıdır; tam bir örnek için bkz: [şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Media.PenLineCap>
