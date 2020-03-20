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
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187331"
---
# <a name="how-to-transform-a-brush"></a>Nasıl yapılır: Fırça Dönüşümü
Bu örnek, iki <xref:System.Windows.Media.Brush> dönüştürme özelliklerini kullanarak nesnelerin <xref:System.Windows.Media.Brush.RelativeTransform%2A> nasıl <xref:System.Windows.Media.Brush.Transform%2A>dönüştürüleceklerini gösterir: ve.  
  
 Aşağıdaki örneklerde <xref:System.Windows.Media.RotateTransform> a, bir <xref:System.Windows.Media.ImageBrush> derecenin içeriğini 45 derece döndürmek için kullanılır.  
  
 Aşağıdaki resimde, <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliğe <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform> uygulanan bir , olmayan ve <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.Brush.Transform%2A> özelliğe uygulanan ile gösterilmektedir.  
  
 ![Fırça RelativeTransform ve Transform ayarları](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Örnek  
 İlk örnek bir <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.Brush.RelativeTransform%2A> . <xref:System.Windows.Media.ImageBrush> Bir <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> <xref:System.Windows.Media.RotateTransform> nesnenin ve özelliklerinin her ikisi de 0,5 olarak ayarlanır, bu da bu içeriğin merkez noktasının göreli koordinatıdır. Sonuç olarak, <xref:System.Windows.Media.ImageBrush> içerik merkezi etrafında döner.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 İkinci örnek de bir; <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.ImageBrush> ancak, bu örnek <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği yerine özelliği kullanır.  
  
 Fırçayı merkezi yle döndürmek için, örnek <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> nesnenin <xref:System.Windows.Media.RotateTransform> özelliklerini ve özelliklerini mutlak koordinatlara ayarlar. Fırça 175'e 90 piksellik bir dikdörtgen boyadığından, dikdörtgenin orta noktası (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Özelliklerin ve <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.Brush.Transform%2A> özelliklerinin nasıl çalıştığına yönelik bir açıklama için [Fırça Dönüşümüne Genel Bakış'a](brush-transformation-overview.md)bakın.  
  
 Tam örnek için [Fırçalar Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)bakın. Fırçalar hakkında daha fazla bilgi için, [Düz Renkler ve Degradeler Genel Bakış ile Boyama](painting-with-solid-colors-and-gradients-overview.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fırça Dönüşümüne Genel Bakış](brush-transformation-overview.md)
- [Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış](painting-with-solid-colors-and-gradients-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
