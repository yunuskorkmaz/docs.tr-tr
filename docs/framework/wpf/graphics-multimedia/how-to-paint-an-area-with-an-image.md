---
title: 'Nasıl yapılır: Görüntü ile bir Alanı Boyama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 4efecc3c8083396d4c06d86d9ece01bd584a1c6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-paint-an-area-with-an-image"></a>Nasıl yapılır: Görüntü ile bir Alanı Boyama
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.ImageBrush> alanı bir görüntü ile boyamak için sınıf. Bir <xref:System.Windows.Media.ImageBrush> tarafından belirtilen tek bir resmi görüntüler kendi <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek paints <xref:System.Windows.Controls.Control.Background%2A> kullanarak düğmesinin bir <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Varsayılan olarak, bir <xref:System.Windows.Media.ImageBrush> boyama alanını tamamen doldurmak için kendi resmini uzatır. Önceki örnekte, görüntü, büyük olasılıkla resim bozulur düğmesi, dolduracak şekilde genişletilir. Bu davranış ayarlayarak denetleyebilirsiniz <xref:System.Windows.Media.TileBrush.Stretch%2A> özelliği <xref:System.Windows.Media.TileBrush> için <xref:System.Windows.Media.Stretch.Uniform> veya <xref:System.Windows.Media.Stretch.UniformToFill>, resmin oranını korumak fırça neden olur.  
  
 Ayarlarsanız <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliklerini bir <xref:System.Windows.Media.ImageBrush>, yinelenen bir desen oluşturabilirsiniz. Aşağıdaki örnek, bir görüntüden oluşturulan bir desen kullanılarak bir düğme boyar.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> sınıfı için bkz: [görüntüleri, çizimler ve görsellerle boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır <xref:System.Windows.Media.ImageBrush> sınıfı. Tam bir örnek için bkz: [ImageBrush örneği](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüler, Çizimler ve Görsellerle Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
