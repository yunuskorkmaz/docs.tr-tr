---
title: 'Nasıl yapılır: Çokgen Öğe Kullanarak Kapalı Şekil Çizme'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 89c78877e196e803f6b4139ffcfa2b4def1a07d7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698227"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>Nasıl yapılır: Çokgen Öğe Kullanarak Kapalı Şekil Çizme
Bu örnekte kullanarak kapalı şekil çizme gösterilmektedir <xref:System.Windows.Shapes.Polygon> öğesi. Kapalı şekil çizme için oluşturma bir <xref:System.Windows.Shapes.Polygon> öğesi ve kullanım kendi <xref:System.Windows.Shapes.Polygon.Points%2A> özelliği bir şeklin köşe belirtmek için. Bir çizgi ilk ve son noktalarına bağlayan otomatik olarak çizilir. Son olarak, belirtin bir <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, veya her ikisini de.  
  
## <a name="example"></a>Örnek  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], noktaları için geçerli sözdizimi virgülle ayrılmış x ve y-koordinatını çiftlerinin boşlukla ayrılmış bir listesini aşağıdaki gibidir.  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 Örnek kullansa da bir <xref:System.Windows.Controls.Canvas> çokgenler içermek için Çokgen öğeler (ve diğer tüm şekil öğelerine) ile kullanabileceğiniz <xref:System.Windows.Controls.Panel> veya <xref:System.Windows.Controls.Control> , metin olmayan içerikleri destekler.  
  
 Bu örnek, daha büyük bir örnek bir parçasıdır; tam bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).
