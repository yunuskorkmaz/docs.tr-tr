---
title: 'Nasıl yapılır: StreamGeometry Kullanarak Şekil Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: 3273b6f45c367afeb8e572d0f68e6774075890c9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361025"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>Nasıl yapılır: StreamGeometry Kullanarak Şekil Oluşturma
<xref:System.Windows.Media.StreamGeometry> Hafif alternatifi <xref:System.Windows.Media.PathGeometry> geometrik şekiller oluşturma. Kullanım bir <xref:System.Windows.Media.StreamGeometry> karmaşık geometri açıklamak gerektiğinde ancak destekleme veri bağlama, animasyon veya değişikliği yükü istemiyorsanız. Örneğin, verimlilik, nedeniyle <xref:System.Windows.Media.StreamGeometry> sınıftır donatıcıları açıklamak için iyi bir seçimdir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir üçgen oluşturmak için öznitelik sözdizimi kullanır. <xref:System.Windows.Media.StreamGeometry> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.StreamGeometry> öznitelik sözdizimi için bkz: [yol işaretleme söz dizimi](path-markup-syntax.md) sayfası.  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte bir <xref:System.Windows.Media.StreamGeometry> kodda bir üçgen tanımlamak için. İlk olarak, örnek, oluşturur bir <xref:System.Windows.Media.StreamGeometry>, ardından alır bir <xref:System.Windows.Media.StreamGeometryContext> ve bu üçgen tanımlamak için kullanır.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte kullanan bir yöntem oluşturur bir <xref:System.Windows.Media.StreamGeometry> ve <xref:System.Windows.Media.StreamGeometryContext> belirtilen parametrelere göre bir geometrik şekil tanımlamak için.  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [PathGeometry Kullanarak Şekil Oluşturma](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [Geometriye Genel Bakış](geometry-overview.md)
