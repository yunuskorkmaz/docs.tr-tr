---
title: "Nasıl yapılır: RectangleGeometry'nin Köşelerini Yuvarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cd857f7ce886095bcbe92ae57c350ce83bb5c7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>Nasıl yapılır: RectangleGeometry'nin Köşelerini Yuvarlama
Köşelerinde yuvarlanacak bir <xref:System.Windows.Media.RectangleGeometry>ayarlayın, <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> ve <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> sıfırdan büyük bir değere özellikleri. Daha büyük değerler, dikdörtgenin yuvarlaklaşır köşeleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, birkaç gösterir <xref:System.Windows.Media.RectangleGeometry> farklı nesneleriyle <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> ve <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> ayarlar. <xref:System.Windows.Media.RectangleGeometry> Nesneler kullanarak görüntülenir <xref:System.Windows.Shapes.Path> öğeleri.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![Dikdörtgenler farklı RadiusX &#47; RadiusY ayarları](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm_rounded")  
Yuvarlanmış köşeli dikdörtgenler  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geometri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Bileşik şekil oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Bir şekli PathGeometry kullanarak oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
