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
ms.openlocfilehash: c56053f2b07d6055deac5097a68fd7b80ad704ba
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452103"
---
# <a name="how-to-create-a-composite-shape"></a>Nasıl yapılır: Bileşik Şekil Oluşturma
Bu örnek, <xref:System.Windows.Media.Geometry> nesneleri kullanarak bileşik şekillerin nasıl oluşturulduğunu ve <xref:System.Windows.Shapes.Path> bir öğesi kullanarak nasıl görüntüleneceğini gösterir. Aşağıdaki örnekte, bir <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>ve bir <xref:System.Windows.Media.RectangleGeometry> bileşik şekil oluşturmak için <xref:System.Windows.Media.GeometryGroup> ile birlikte kullanılır. Geometriler daha sonra bir <xref:System.Windows.Shapes.Path> öğesi kullanılarak çizilir.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 Aşağıdaki çizimde, önceki örnekte oluşturulan Şekil gösterilmektedir.  
  
 ![GeometryGroup kullanılarak oluşturulan bileşik geometri](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")  
Bileşik geometri  
  
 <xref:System.Windows.Media.PathGeometry>kullanılarak çokgenler ve eğri kesimli şekiller gibi daha karmaşık şekiller oluşturulabilir. <xref:System.Windows.Media.PathGeometry>kullanarak şekil oluşturmayı gösteren bir örnek için, bkz. [PathGeometry kullanarak şekil oluşturma](how-to-create-a-shape-by-using-a-pathgeometry.md).  Bu örnek, <xref:System.Windows.Shapes.Path> bir öğesi kullanarak ekrana bir şekil çizer, ancak <xref:System.Windows.Media.Geometry> nesneleri, bir <xref:System.Windows.Media.GeometryDrawing> veya bir <xref:System.Windows.Media.DrawingContext>içeriğini anlatmak için de kullanılabilir. Bunlar, kırpma ve isabet testi için de kullanılabilir.  
  
 Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).
