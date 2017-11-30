---
title: "Nasıl yapılır: Satır veya Segment Sonunda Uç Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e062b82e698a99705a2b06588aa9aae3a0c93157
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
