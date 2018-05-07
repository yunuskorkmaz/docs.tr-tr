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
ms.openlocfilehash: 5caa00a378101ff4dff7745a18c3ec8905cc168b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-transform-a-brush"></a>Nasıl yapılır: Fırça Dönüşümü
Bu örnek nasıl dönüştürüleceğini gösterir <xref:System.Windows.Media.Brush> iki dönüşüm özelliklerini kullanarak nesneleri: <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 Aşağıdaki örnekler bir <xref:System.Windows.Media.RotateTransform> içeriğini döndürmek için bir <xref:System.Windows.Media.ImageBrush> 45 derece.  
  
 Aşağıdaki çizimde gösterildiği <xref:System.Windows.Media.ImageBrush> olmadan bir <xref:System.Windows.Media.RotateTransform>, ile <xref:System.Windows.Media.RotateTransform> uygulanan <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği ile <xref:System.Windows.Media.RotateTransform> uygulanan <xref:System.Windows.Media.Brush.Transform%2A> özelliği.  
  
 ![Fırça göreli dönüştürmesi ve dönüşüm ayarları](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Örnek  
 İlk örnek geçerli bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği bir <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform.CenterX%2A> Ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini bir <xref:System.Windows.Media.RotateTransform> her ikisi de ayarlanır, bu içeriğin orta noktasının göreli koordinatı olan 0,5 olarak nesne. Sonuç olarak, <xref:System.Windows.Media.ImageBrush> içeriği ortasından döner.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 İkinci örnek de geçerlidir bir <xref:System.Windows.Media.RotateTransform> için bir <xref:System.Windows.Media.ImageBrush>; ancak, bu örnek kullanır <xref:System.Windows.Media.Brush.Transform%2A> özelliği yerine <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği.  
  
 Kendi Merkezi hakkında fırça döndürmek için örnek ayarlar <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini <xref:System.Windows.Media.RotateTransform> mutlak koordinatları nesnesine. Fırça 175 90 piksel olan bir dikdörtgen boyar çünkü dikdörtgenin merkez noktasıdır (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Bir açıklaması için nasıl <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A> özellikleri çalışma, bkz [fırça dönüşümüne genel bakış](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Tam bir örnek için bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973). Fırçalar hakkında daha fazla bilgi için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fırça Dönüşümüne Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
