---
title: "Nasıl yapılır: StreamGeometry Kullanarak Şekil Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a333fd6c1906eaea2c8eaf2c3b07502b5a9c4d40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>Nasıl yapılır: StreamGeometry Kullanarak Şekil Oluşturma
<xref:System.Windows.Media.StreamGeometry>için hafif alternatif <xref:System.Windows.Media.PathGeometry> geometrik şekiller oluşturma. Kullanım bir <xref:System.Windows.Media.StreamGeometry> karmaşık geometri açıklamak gerektiğinde ancak veri bağlama, animasyon veya değişimi destekleme ek yükünü istemiyorsanız. Örneğin, verimlilik nedeniyle <xref:System.Windows.Media.StreamGeometry> sınıftır donarıcıları açıklamak için iyi bir seçimdir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir üçgen oluşturmak için öznitelik sözdizimini kullanır. <xref:System.Windows.Media.StreamGeometry> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.StreamGeometry> öznitelik sözdizimi, bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) sayfası.  
  
## <a name="example"></a>Örnek  
 Sonraki örnek kullanan bir <xref:System.Windows.Media.StreamGeometry> kodda bir üçgen tanımlamak için. İlk olarak, örnek oluşturur bir <xref:System.Windows.Media.StreamGeometry>, ardından alacağı bir <xref:System.Windows.Media.StreamGeometryContext> ve üçgen tanımlamak için kullanır.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnek kullanan bir yöntem oluşturur bir <xref:System.Windows.Media.StreamGeometry> ve <xref:System.Windows.Media.StreamGeometryContext> belirtilen parametrelere göre bir geometrik şekil tanımlamak için.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.StreamGeometryContext>  
 [PathGeometry Kullanarak Şekil Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)  
 [Geometriye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
