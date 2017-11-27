---
title: "Nasıl yapılır: Çizgi Çizme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4911aea91416fb84e9a18d54c145b494737ef9dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line"></a>Nasıl yapılır: Çizgi Çizme
Bu örnek nasıl kullanarak satırları çizileceğini gösterir <xref:System.Windows.Shapes.Line> öğesi.  
  
 Bir çizgi çizmek için oluşturma bir <xref:System.Windows.Shapes.Line> öğesi. Kullanın, <xref:System.Windows.Shapes.Line.X1%2A> ve <xref:System.Windows.Shapes.Line.Y1%2A> özellikleri, başlangıç noktası; ve kullanmak için kendi <xref:System.Windows.Shapes.Line.X2%2A> ve <xref:System.Windows.Shapes.Line.Y2%2A> uç noktasını ayarlamak için özellikler. Son olarak ayarlamak, <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> bir vuruş olmadan çizgi görünmez olduğundan.  
  
 Ayarı <xref:System.Windows.Shapes.Shape.Fill%2A> öğesi bir satır için bir satır hiçbir iç kısmı olmadığından hiçbir etkisi vardır.  
  
 Aşağıdaki örnek içinde üç çizgi çizilmiştir bir <xref:System.Windows.Controls.Canvas> öğesi.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 Bu örnek daha büyük bir örneğin parçasıdır; tam bir örnek için bkz: [şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Shapes.Line>  
 [Şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037)
