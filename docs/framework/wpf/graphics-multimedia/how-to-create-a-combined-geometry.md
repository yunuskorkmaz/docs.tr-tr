---
title: "Nasıl yapılır: Birleşik Geometri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2be0471f27d26b145cc29847a08bf3bc3b1d51ff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-combined-geometry"></a>Nasıl yapılır: Birleşik Geometri Oluşturma
Bu örnek nasıl geometri birleştirileceğini gösterir. İki geometri birleştirmek için kullanın bir <xref:System.Windows.Media.CombinedGeometry> nesnesi. Ayarlama, <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> birleştirmek ve ayarlamak için iki geometri özelliklerle <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> geometri birlikte nasıl birleştirileceğini belirleyen, özellik için `Union`, `Intersect`, `Exclude`, veya `Xor`.  
  
 İki veya daha fazla geometri bileşik geometri oluşturmak için bir <xref:System.Windows.Media.GeometryGroup>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> geometri birleştirme modu ile tanımlanan `Exclude`.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![Birleştirme modu sonuçları tut](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")  
Birleşik Geometri dışlama  
  
 Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Intersect`.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![Birleştirme modu INTERSECT sonuçları](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")  
Birleşik Geometri kesişimi  
  
 Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Union`.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Birleştirme modu UNION sonuçları](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
Birleşik Geometri Birliği  
  
 Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Xor`.  Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Birleştirme modu Xor sonuçları](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
Birleşik Geometri Xor
