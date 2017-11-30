---
title: "Nasıl yapılır: Elips Yay Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eeb93cefd2e55e80f27922feab788698653f405e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-elliptical-arc"></a>Nasıl yapılır: Elips Yay Oluşturma
Bu örnek nasıl elips yay çizileceğini gösterir. Elips yay oluşturmak üzere kullanmanız <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, ve <xref:System.Windows.Media.ArcSegment> sınıfları.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, elips yay (10,100) dan (200,100) çizilir. Yayı sahip bir <xref:System.Windows.Media.ArcSegment.Size%2A> 100 50 aygıttan bağımsız piksel tarafından bir <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 derece bir <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ayarıyla `true`ve bir <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> , <xref:System.Windows.Media.SweepDirection.Counterclockwise>.  
  
 [xaml]  
  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu açıklamak için öznitelik sözdizimini kullanabilirsiniz.  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 [xaml]  
  
 (Bu öznitelik sözdizimi gerçekte oluşturur Not bir <xref:System.Windows.Media.StreamGeometry>, hafifletilmiş sürümü bir <xref:System.Windows.Media.PathGeometry>. Daha fazla bilgi için bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) sayfası.)  
  
 İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], açıkça nesne etiketleri kullanılarak elips yay çizebilirsiniz. Aşağıdaki önceki eşdeğerdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 Bu örnek daha büyük bir örneğin parçasıdır. Tam bir örnek için bkz: [geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İkinci dereceden Bezier eğrisi oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [Küp Bezier eğrisi oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
