---
title: 'Nasıl yapılır: Bileşik Şekil Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: 6bb2a8a32938682af52343b971b840dbed16bcef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559981"
---
# <a name="how-to-create-a-composite-shape"></a>Nasıl yapılır: Bileşik Şekil Oluşturma
Bu örnek kullanarak bileşik şekillerin oluşturulacağını gösterir <xref:System.Windows.Media.Geometry> nesneleri ve bunları görüntülemek kullanarak bir <xref:System.Windows.Shapes.Path> öğesi. Aşağıdaki örnekte, bir <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>ve bir <xref:System.Windows.Media.RectangleGeometry> ile kullanılan bir <xref:System.Windows.Media.GeometryGroup> bileşik bir şekil oluşturmak için. Kullanılarak geometri çizilir bir <xref:System.Windows.Shapes.Path> öğesi.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 Aşağıdaki çizimde önceki örnekte oluşturulan şekli gösterir.  
  
 ![GeometryGroup kullanılarak oluşturulan bileşik geometri](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Bileşik geometri  
  
 Kullanarak çokgenler ve eğri kesimli şekiller gibi daha karmaşık şekiller oluşturulabilir bir <xref:System.Windows.Media.PathGeometry>. Kullanarak bir şekil oluşturmak nasıl gösteren bir örnek için bir <xref:System.Windows.Media.PathGeometry>, bkz: [PathGeometry kullanarak bir şekil oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  Bu örnek kullanarak ekrana şekil işler ancak bir <xref:System.Windows.Shapes.Path> öğesi, <xref:System.Windows.Media.Geometry> nesnelerini ayrıca içeriğini tanımlamak için kullanılabilecek bir <xref:System.Windows.Media.GeometryDrawing> veya <xref:System.Windows.Media.DrawingContext>. Bunlar, kırpma ve isabet testi için de kullanılabilir.  
  
 Bu örnek daha büyük bir parçasıdır; tam bir örnek için bkz: [geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989).
