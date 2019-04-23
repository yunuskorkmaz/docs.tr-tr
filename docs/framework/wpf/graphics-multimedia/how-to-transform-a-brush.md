---
title: 'Nasıl yapılır: Fırça Dönüşümü'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: a83f3b1c046e94faa8816e8c310f438b4711048a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163013"
---
# <a name="how-to-transform-a-brush"></a>Nasıl yapılır: Fırça Dönüşümü
Bu örnek nasıl dönüştürüleceğini gösterir <xref:System.Windows.Media.Brush> iki dönüştürme özelliklerini kullanarak nesneleri: <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 Aşağıdaki örneklerde bir <xref:System.Windows.Media.RotateTransform> içeriğini döndürmek için bir <xref:System.Windows.Media.ImageBrush> 45 derece.  
  
 Aşağıdaki çizimde gösterildiği <xref:System.Windows.Media.ImageBrush> olmadan bir <xref:System.Windows.Media.RotateTransform>, ile <xref:System.Windows.Media.RotateTransform> uygulanan <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği ile <xref:System.Windows.Media.RotateTransform> uygulanan <xref:System.Windows.Media.Brush.Transform%2A> özelliği.  
  
 ![Fırça RelativeTransform ve dönüşüm ayarları](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Örnek  
 İlk örnek geçerli bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği bir <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform.CenterX%2A> Ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini bir <xref:System.Windows.Media.RotateTransform> her ikisi de ayarlanmış bu içeriğin orta noktasının göreli koordinatı 0,5 nesne. Sonuç olarak, <xref:System.Windows.Media.ImageBrush> içeriği ortasından döndürür.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 İkinci örnek de geçerlidir bir <xref:System.Windows.Media.RotateTransform> için bir <xref:System.Windows.Media.ImageBrush>; ancak bu örnekte <xref:System.Windows.Media.Brush.Transform%2A> özelliği yerine <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği.  
  
 Örnek merkezi fırçayı döndürmek için ayarlar <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini <xref:System.Windows.Media.RotateTransform> mutlak koordinatlara nesne. Fırça 175 90 piksel bir dikdörtgen boyar, merkez noktasını dikdörtgenin olduğundan (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Nasıl bir açıklaması için <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A> özellikleri çalışma, bkz [fırça dönüşümüne genel bakış](brush-transformation-overview.md).  
  
 Tam bir örnek için bkz. [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973). Fırçalar hakkında daha fazla bilgi için bkz. [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fırça Dönüşümüne Genel Bakış](brush-transformation-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
