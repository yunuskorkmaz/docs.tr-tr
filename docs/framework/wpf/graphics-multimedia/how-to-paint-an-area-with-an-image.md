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
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186059"
---
# <a name="how-to-paint-an-area-with-an-image"></a>Nasıl yapılır: Görüntü ile bir Alanı Boyama
Bu örnek, bir <xref:System.Windows.Media.ImageBrush> alanı görüntüyle boyamak için sınıfın nasıl kullanılacağını gösterir. Bir <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.ImageBrush.ImageSource%2A> özelliği tarafından belirtilen tek bir görüntü görüntüler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Media.ImageBrush>düğmenin bir .  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Varsayılan olarak, <xref:System.Windows.Media.ImageBrush> bir resim tamamen boyama alanı doldurmak için kendi görüntü uzanır. Önceki örnekte, görüntü düğmeyi doldurmak için gerilmiş ve büyük olasılıkla görüntüyü bozuyor. Fırçanın <xref:System.Windows.Media.TileBrush.Stretch%2A> görüntünün en boy <xref:System.Windows.Media.TileBrush> oranını <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>korumasına neden olan özelliğini ayarlayarak bu davranışı denetleyebilirsiniz.  
  
 Bir <xref:System.Windows.Media.TileBrush.Viewport%2A> ,'nin <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliklerini <xref:System.Windows.Media.ImageBrush>ve özelliklerini ayarlarsanız, yinelenen bir desen oluşturabilirsiniz. Aşağıdaki örnek, görüntüden oluşturulan bir desen kullanarak bir düğmeyi boyar.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <xref:System.Windows.Media.ImageBrush> Sınıf hakkında daha fazla bilgi için [Resim, Çizim ve Görsellerle Boyama'ya](painting-with-images-drawings-and-visuals.md)bakın.  
  
 Bu kod örneği, <xref:System.Windows.Media.ImageBrush> sınıf için sağlanan daha büyük bir örneğin bir parçasıdır. Tam örnek için [ImageBrush Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Çizimler ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)
