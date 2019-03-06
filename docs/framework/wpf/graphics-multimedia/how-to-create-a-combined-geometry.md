---
title: 'Nasıl yapılır: Birleşik Geometri Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: c5ebe87abd4c2cf70f8fa17f1fcc773293f3ad27
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364794"
---
# <a name="how-to-create-a-combined-geometry"></a>Nasıl yapılır: Birleşik Geometri Oluşturma
Bu örnek nasıl geometriler birleştirileceğini gösterir. İki geometri birleştirmek için kullanın. bir <xref:System.Windows.Media.CombinedGeometry> nesne. Ayarlama, <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> Özellikleri birleştirmek ve ayarlamak için iki geometriler ile <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> geometriler birlikte nasıl birleştirileceğini belirleyen, özelliği için `Union`, `Intersect`, `Exclude`, veya `Xor`.  
  
 Birleşik Geometri iki veya daha fazla geometri oluşturmak için bir <xref:System.Windows.Media.GeometryGroup>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> geometri birleştirme modu ile tanımlanan `Exclude`.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![Birleştirme modu sonuçları tut](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")  
Birleşik Geometri dışlama  
  
 Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Intersect`.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![INTERSECT sonuçlarını birleştirmek modu](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")  
Birleşik Geometri kesişimi  
  
 Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Union`.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Birleştirme modu UNION sonuçları](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
Birleşik Geometri birleşim  
  
 Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Xor`.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor sonuçlarını birleştirmek modu](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
Birleşik Geometri Xor
