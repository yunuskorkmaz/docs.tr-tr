---
title: "Nasıl yapılır: Çoklu Çizgi Öğesi Kullanarak Çoklu Çizgi Çizme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b0b027aa34b310413fa02e81149292fabb40f79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a>Nasıl yapılır: Çoklu Çizgi Öğesi Kullanarak Çoklu Çizgi Çizme
Bu örnek, bir dizi bağlı çizgilere kullanmaktır bir çoklu çizgi çizmek gösterilmektedir <xref:System.Windows.Shapes.Polyline> öğesi.  
  
 Bir çoklu çizgi çizmek için oluşturma bir <xref:System.Windows.Shapes.Polyline> öğesi ve kullanım kendi <xref:System.Windows.Shapes.Polyline.Points%2A> Şekil köşeleri belirtmek için özellik. Son olarak, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özelliklerini çoklu çizgi açıklamak için bir vuruş olmadan çizgi görünmez olduğundan ana hatlarını vermektedir.  
  
> [!NOTE]
>  Çünkü <xref:System.Windows.Shapes.Polyline> öğesi kapalı bir şekil değil <xref:System.Windows.Shapes.Shape.Fill%2A> özelliğinin hiçbir etkisi, Şekil anahat kapatsanız bile. İle kapalı bir şekil oluşturmak için bir <xref:System.Windows.Shapes.Shape.Fill%2A>, kullanan bir <xref:System.Windows.Shapes.Polygon> öğesi.  
  
 Aşağıdaki örnekte iki çizer <xref:System.Windows.Shapes.Polyline> öğeler içinde bir <xref:System.Windows.Controls.Canvas>.  
  
## <a name="example"></a>Örnek  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], noktaları için geçerli sözdizimi virgülle ayrılmış x - ve y koordinatını çiftleri boşlukla ayrılmış bir listesi verilmiştir.  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 Bu örnek kullansa da bir <xref:System.Windows.Controls.Canvas> kullansa içerecek şekilde çoklu çizgi öğelerini (ve diğer tüm şekil öğelerini) ile kullanabileceğiniz <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> metin dışı içeriği destekler.  
  
 Bu örnek daha büyük bir örneğin parçasıdır; tam bir örnek için bkz: [şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [Şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [WPF’de Şekiller ve Temel Çizimlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
